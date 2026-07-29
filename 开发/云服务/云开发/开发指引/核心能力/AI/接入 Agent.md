# [#](#Agent-接入) Agent 接入

Agent（智能体）是基于大模型构建的、能够完成特定任务的 AI 应用。与直接调用大模型不同，Agent 可以使用工具、访问知识库、执行多步推理，适合构建复杂的对话应用。

在小程序中通过 `wx.cloud.extend.AI` 调用云开发 Agent，实现智能对话。

- 小程序基础库 ≥ **3.7.1**
- 已开通云开发环境
- 已在 [云开发控制台 → AI → Agent](https://tcb.cloud.tencent.com/dev#/ai?tab=agent) 中创建 Agent

## [#](#初始化) 初始化

```
wx.cloud.init({
  env: "<云开发环境ID>",
});

const ai = wx.cloud.extend.AI;
```

## [#](#基本调用) 基本调用

使用 `ai.bot.sendMessage()` 与 Agent 进行对话：

```
const res = await ai.bot.sendMessage({
  data: {
    botId: "<你的 Agent ID>",
    threadId: "thread_" + Date.now().toString(),
    runId: "run_" + Date.now().toString(),
    messages: [
      {
        id: String(Date.now()),
        role: "user",
        content: "你好，请介绍一下你自己",
      },
    ],
    tools: [],
    context: [],
    state: {},
    forwardedProps: {},
  },
});

let response = "";
for await (const event of res.eventStream) {
  const data = JSON.parse(event.data);
  switch (data.type) {
    case "TEXT_MESSAGE_CONTENT":
      response += data.delta;
      break;
    case "RUN_FINISHED":
      console.log("对话结束");
      break;
    case "RUN_ERROR":
      console.error("运行出错:", data.message);
      break;
  }
}

console.log("完整回复:", response);
```

## [#](#请求参数) 请求参数

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| botId | string | 是 | Agent ID，在控制台创建 Agent 后获取 |
| threadId | string | 是 | 会话 ID，同一个 threadId 属于同一个会话 |
| runId | string | 是 | 本次运行 ID，每次调用使用不同的 runId |
| messages | array | 是 | 消息列表，包含用户发送的消息 |
| tools | array | 否 | 自定义工具列表，默认为空数组 |
| context | array | 否 | 上下文信息，默认为空数组 |
| state | object | 否 | 自定义状态，默认为空对象 |
| forwardedProps | object | 否 | 透传属性，默认为空对象 |

### [#](#messages-格式) messages 格式

```
{
  id: String(Date.now()),  // 消息唯一 ID
  role: "user",            // 消息角色：user
  content: "用户输入内容"   // 消息内容
}
```

## [#](#响应事件类型) 响应事件类型

Agent 通过 SSE（Server-Sent Events）流式返回事件，主要事件类型：

| 事件类型 | 说明 | 关键字段 |
| --- | --- | --- |
| `TEXT_MESSAGE_CONTENT` | 文本内容增量 | `delta` — 文本片段 |
| `RUN_STARTED` | Agent 开始运行 | — |
| `RUN_FINISHED` | Agent 运行结束 | — |
| `RUN_ERROR` | 运行出错 | `message` — 错误信息 |
| `TOOL_CALL_START` | 开始调用工具 | `toolCallId` — 工具调用 ID；`toolCallName` — 工具名称 |
| `TOOL_CALL_ARGS` | 工具参数增量 | `toolCallId`；`delta` — 参数 JSON 片段（同一 `toolCallId` 需按顺序拼接） |
| `TOOL_CALL_END` | 工具调用结束 | `toolCallId` — 工具调用 ID（注意：此事件不含执行结果） |
| `TOOL_CALL_RESULT` | 工具执行结果 | `toolCallId`；`content` — 工具返回结果 |

> 完整的事件类型定义参见 [Agent HTTP 协议文档](https://docs.cloudbase.net/ai/agent/http-agent-protocol#响应事件)。

## [#](#多轮对话) 多轮对话

Agent 使用 `threadId` 来管理会话。同一个 `threadId` 下的对话共享上下文，实现多轮连续对话：

```
Page({
  data: {
    messages: [],
    threadId: "",
    isLoading: false,
  },

  onLoad() {
    // 创建一个新会话
    this.setData({ threadId: "thread_" + Date.now().toString() });
  },

  async sendMessage(userInput) {
    const { messages, threadId } = this.data;

    const userMsg = {
      id: String(Date.now()),
      role: "user",
      content: userInput,
    };

    this.setData({
      messages: [...messages, userMsg, { role: "assistant", content: "" }],
      isLoading: true,
    });

    try {
      const ai = wx.cloud.extend.AI;
      const res = await ai.bot.sendMessage({
        data: {
          botId: "<你的 Agent ID>",
          threadId: threadId, // 使用同一个 threadId 实现多轮对话
          runId: "run_" + Date.now().toString(), // 每次调用使用新的 runId
          messages: [userMsg], // 只传当前消息，历史由 Agent 服务端管理
          tools: [],
          context: [],
          state: {},
          forwardedProps: {},
        },
      });

      let assistantContent = "";
      for await (const event of res.eventStream) {
        const data = JSON.parse(event.data);
        if (data.type === "TEXT_MESSAGE_CONTENT") {
          assistantContent += data.delta;
          const updatedMessages = [...messages, userMsg, { role: "assistant", content: assistantContent }];
          this.setData({ messages: updatedMessages });
        }
      }
    } catch (error) {
      console.error("调用失败:", error);
    } finally {
      this.setData({ isLoading: false });
    }
  },

  // 新建会话
  newConversation() {
    this.setData({
      messages: [],
      threadId: "thread_" + Date.now().toString(),
    });
  },
});
```

> **与大模型多轮对话的区别：** 大模型需要在每次请求中传入完整的历史消息，而 Agent 的历史消息由服务端管理，客户端每次只需传入当前消息，通过 `threadId` 关联同一会话。

## [#](#错误处理) 错误处理

```
const res = await ai.bot.sendMessage({ data: { /* ... */ } });

for await (const event of res.eventStream) {
  const data = JSON.parse(event.data);

  switch (data.type) {
    case "TEXT_MESSAGE_CONTENT":
      // 正常文本内容
      break;

    case "RUN_ERROR":
      // 运行出错，展示错误信息
      console.error("Agent 运行出错:", data.message);
      wx.showToast({ title: "请求出错", icon: "error" });
      break;

    case "RUN_FINISHED":
      // 运行结束
      break;
  }
}
```

## [#](#获取-Agent-ID) 获取 Agent ID

在 [云开发控制台 → AI → Agent](https://tcb.cloud.tencent.com/dev#/ai?tab=agent) 中创建 Agent 后，可以获取对应的 Agent ID：

![](https://res8.wxqcloud.qq.com.cn/wxdoc/527bff19-9e77-4b97-91dc-e3e8eec1e0e2.png)

## [#](#Agent-与大模型的对比) Agent 与大模型的对比

| 特性 | 大模型（createModel） | Agent（bot.sendMessage） |
| --- | --- | --- |
| 适用场景 | 简单问答、文本生成 | 复杂对话、任务执行 |
| 会话管理 | 客户端维护 messages 历史 | 服务端通过 threadId 管理 |
| 工具调用 | 不支持 | 支持（联网搜索、知识库等） |
| 自定义能力 | 通过 system prompt 设定 | 在控制台配置指令、工具、知识库 |
| 返回方式 | 文本流 | SSE 事件流（含工具调用事件） |

Incorrect translation.