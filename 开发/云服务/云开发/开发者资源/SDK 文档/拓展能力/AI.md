# [#](#wx-cloud-extend-AI) wx.cloud.extend.AI

> 支持端：小程序、云函数

微信小程序基础库版本 `3.15.1` 及以上，支持通过微信云开发的 `wx.cloud.extend.AI` 扩展接口调用 cloudbase 提供的 DeepSeek、混元、Kimi、GLM、Minimax 等最新模型。

## [#](#初始化) 初始化

在使用 AI 相关能力前，需要传入云开发环境进行初始化。

```
wx.cloud.init({
  env: "<你的环境ID>",
});
```

初始化完毕后，即可通过 `wx.cloud.extend.AI` 使用扩展接口来调用 AI 相关能力。

## [#](#大模型) 大模型

### [#](#AI-createModel) AI.createModel()

创建指定的 AI 模型。

#### [#](#使用示例) 使用示例

传入模型提供商字符串：

```
const model = wx.cloud.extend.AI.createModel("cloudbase");
```

传入 `ModelDefinition` 对象（基础库 `3.15.1` 及以上支持）：

```
const model = wx.cloud.extend.AI.createModel({
  modelName: "custom-model",
  modelPath: "/v1/chat/completions",
  extractPath: "choices[0].delta.content",
  reasoningPath: "choices[0].delta.reasoning_content",
});
```

#### [#](#类型声明) 类型声明

```
function createModel(model: string | ModelDefinition): ChatModel;

interface ModelDefinition {
  modelName: string;
  modelPath: string;
  extractPath: string;
  reasoningPath?: string;
}
```

#### [#](#参数) 参数

| 参数名 | 必填 | 类型 | 说明 |
| --- | --- | --- | --- |
| model | 是 | `string \| ModelDefinition` | 模型名称字符串或模型定义对象 |
| model.modelName | 是 | `string` | 模型名称 |
| model.modelPath | 是 | `string` | 模型请求路径 |
| model.extractPath | 是 | `string` | 文本内容提取路径 |
| model.reasoningPath | 否 | `string` | 推理内容提取路径 |

返回一个提供 AI 生成文本能力的对象。

### [#](#ChatModel-streamText) ChatModel.streamText()

以流式调用大模型生成文本。流式调用时，生成的文本及其他响应数据会通过 [SSE](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events) 返回，该接口的返回值对 SSE 做了不同程度的封装，开发者能根据实际需求获取到文本流和完整数据流。

#### [#](#streamText-使用示例) streamText 使用示例

```
// 连接模型提供商
const provider = wx.cloud.extend.AI.createModel("cloudbase"); 
const res = await provider.streamText({
  data: {
    model: "hy3-preview",
    messages: [
      {
        role: "user",
        content: "hi"
      }
    ]
  }
});

for await (let str of res.textStream) {
  // 打印生成的文本
  console.log(str); 
}
for await (let event of res.eventStream) {
  // 打印每次返回的完整数据
  console.log(event); 

  // 当大模型结束传输时，通常会发一条 [DONE] 数据，在此之后即可停止循环
  if (event.data === "[DONE]") {
    break;
  }
}
```

#### [#](#streamText-类型声明) streamText 类型声明

```
function streamText(props: StreamTextInput): Promise<StreamTextResult>;

interface StreamTextResult {
  eventStream: EventStream;
  textStream: TextStream;
}

interface StreamTextInput {
  data: unknown;
  onEvent?: OnEvent;
  onText?: OnText;
  onFinish?: OnFinish;
}

interface OnEvent {
  (prop: { data: string }): unknown;
}

interface OnText {
  (text: string): unknown;
}

interface OnFinish {
  (text: string): unknown;
}

interface EventStream {
  [Symbol.asyncIterator](): AsyncIterator<{
    event?: unknown;
    id?: unknown;
    data: string;
  }>;
}

interface TextStream {
  [Symbol.asyncIterator](): AsyncIterator<string>;
}
```

#### [#](#参数-2) 参数

| 参数名 | 必填 | 类型 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| props.data | 是 | `unknown` | `{model: "deepseek-v4-flash", messages: [{ role: "user", content: "你好，请你介绍一下李白" }]}` | 各家大模型的调用参数不同，请根据实际调用模型传入正确的参数。 |
| props.tools | 否 | `object` | -- | 工具调用相关参数 |
| props.tools.autoExecute | 否 | `boolean` | `true` | 是否自动调用工具，默认为 `true` |
| props.tools.maxStep | 否 | `number` | `10` | 最大自动执行的次数，默认为 10 次 |
| props.tools.list | 否 | `Array` | -- | 工具列表 |
| `props.tools.list[n].name` | 是 | `string` | `"get_weather"` | 工具名称 |
| `props.tools.list[n].description` | 否 | `string` | `返回某个城市的某天的温度信息。调用示例：get_weather({city: '北京',date: '03-19'})` | 工具描述 |
| `props.tools.list[n].fn` | 是 | `function` | `({ city, date }) => city + "在" + date + "的温度是：" + (20 + (Math.random() * 10))` | 工具执行的回调函数 |
| `props.tools.list[n].parameters` | 否 | `{"type":"object","properties":{"city":{"type":"string","description":"要查询的城市"},"date":{"type":"string","description":"要查询的日期"}},"required":["city","date"]}` | -- | 工具执行回调函数的入参 schema 定义 |
| props.tools.onToolEvent | 否 | `function` | `console.warn` | 监听大模型执行 tool\_call 的事件 |
| props.onText | 否 | `(text: string) => unknown;` | `(text) => console.log(text)` | 接收到新文本返回时触发的回调函数，参数为增量的文本 |
| props.onEvent | 否 | `(prop: { data: string }) => unknown;` | `({data}) => console.log(data)` | 接收到新事件返回时触发的回调函数，参数为事件，prop.data 为此次事件包含的数据 |
| props.onFinish | 否 | `(text: string) => unknown;` | `(text) => console.log(text)` | 当本次调用完全结束时触发的回调函数，参数为本次调用返回的完整文本 |

#### [#](#返回值) 返回值

| StreamTextResult 属性名 | 类型 | 说明 |
| --- | --- | --- |
| textStream | `AsyncIterable<string>` | 以流式返回的大模型生成文本，可参考使用示例获取到生成的增量文本。 |
| eventStream | `AsyncIterable<{data: string, event?: unknown, id?: unknown}>` | 以流式返回的大模型响应数据，可参考使用示例获取到生成的增量数据。由于各家大模型响应值互有出入，请根据实际情况合理使用。 |

### [#](#ChatModel-generateText) ChatModel.generateText()

调用大模型生成文本。

#### [#](#使用示例-2) 使用示例

```
// 连接模型提供商
const provider = wx.cloud.extend.AI.createModel("cloudbase"); 
const res = await provider.generateText({
  model: "hy3-preview",
  messages: [{ role: "user", content: "你好" }],
});
console.log(res);
// {
//   "id": "27dae91f4e9a4777782c61f89acf8ea4",
//   "object": "chat.completion",
//   "created": 1737602298,
//   "model": "hy3-preview",
//   "system_fingerprint": "",
//   "choices": [
//     {
//       "index": 0,
//       "message": {
//         "role": "assistant",
//         "content": "你好！很高兴与你交流。请问有什么我可以帮助你的吗？无论是关于生活、工作、学习还是其他方面的问题，我都会尽力为你提供帮助。"
//       },
//       "finish_reason": "stop"
//     }
//   ],
//   "usage": {
//     "prompt_tokens": 3,
//     "completion_tokens": 33,
//     "total_tokens": 36
//   },
//   "note": "以上内容为AI生成，不代表开发者立场，请勿删除或修改本标记"
// }
console.log(res.choices[0].message.content);
// 你好！很高兴与你交流。请问有什么我可以帮助你的吗？无论是关于生活、工作、学习还是其他方面的问题，我都会尽力为你提供帮助。
```

#### [#](#类型声明-2) 类型声明

```
function generateText(data: unknown): Promise<unknown>;
```

#### [#](#参数-3) 参数

| 参数名 | 必填 | 类型 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| data | 是 | unknown | `{model: "deepseek-v4-flash", messages: [{ role: "user", content: "你好，请你介绍一下李白" }]}` | 各家大模型的调用参数不同，请根据实际调用模型传入正确的参数。 |

#### [#](#返回值-2) 返回值

该接口直接返回实际调用大模型的响应值，需要根据实际响应内容解析出需要的数据。参见上文使用示例。

## [#](#Agent) Agent

### [#](#AI-bot-sendMessage) AI.bot.sendMessage()

与 Agent 进行对话。

#### [#](#请求参数说明) 请求参数说明

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| `threadId` | string | 否 | 会话 ID，用于多轮对话 |
| `runId` | string | 否 | 本次运行 ID |
| `messages` | array | 是 | 消息列表 |
| `tools` | array | 否 | 前端工具定义 |
| `context` | array | 否 | 上下文信息 |
| `forwardedProps` | object | 否 | 透传参数 |

#### [#](#消息格式) 消息格式

```
interface Message {
  id: string;           // 消息 ID
  role: "user" | "assistant" | "system" | "tool";
  content: string;      // 消息内容
  name?: string;        // 工具名称（role 为 tool 时）
  toolCallId?: string;  // 工具调用 ID（role 为 tool 时）
}
```

#### [#](#响应格式) 响应格式

响应采用 SSE 格式，每个事件以 `data:` 开头：

```
data: {"type":"TEXT_MESSAGE_START","messageId":"msg-1"}

data: {"type":"TEXT_MESSAGE_CONTENT","messageId":"msg-1","delta":"你好"}

data: {"type":"TEXT_MESSAGE_END","messageId":"msg-1"}

data: {"type":"RUN_FINISHED"}
```

#### [#](#事件类型) 事件类型

| 事件类型 | 说明 |
| --- | --- |
| `RUN_STARTED` | Agent 开始运行 |
| `RUN_FINISHED` | Agent 运行结束 |
| `RUN_ERROR` | Agent 运行出错 |
| `TEXT_MESSAGE_START` | 文本消息开始 |
| `TEXT_MESSAGE_CONTENT` | 文本消息内容（增量） |
| `TEXT_MESSAGE_END` | 文本消息结束 |
| `TOOL_CALL_START` | 工具调用开始 |
| `TOOL_CALL_ARGS` | 工具调用参数（增量） |
| `TOOL_CALL_END` | 工具调用结束 |
| `STATE_SNAPSHOT` | 状态快照 |
| `STATE_DELTA` | 状态增量更新 |
| `MESSAGES_SNAPSHOT` | 消息快照 |
| `STEP_STARTED` | 步骤开始 |
| `STEP_FINISHED` | 步骤结束 |

更多用法请参考 [云开发 Agent 文档](https://docs.cloudbase.net/ai/agent-development/protocol)。

Incorrect translation.