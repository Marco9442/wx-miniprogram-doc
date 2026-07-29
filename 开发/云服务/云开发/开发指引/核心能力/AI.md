# [#](#快速开始) 快速开始

5 分钟在小程序中接入云开发 AI 能力，实现一个最简单的 AI 对话。

## [#](#准备工作) 准备工作

1. 已注册微信小程序账号，并创建本地小程序项目
2. 小程序基础库 ≥ **3.15.1**
3. 已开通云开发环境，并在 [控制台 → AI → 生文模型](https://tcb.cloud.tencent.com/dev#/ai?tab=text-aiModel) 中开启所需模型

## [#](#第-1-步：初始化云开发) 第 1 步：初始化云开发

在 `app.js` 的 `onLaunch` 中初始化云开发环境：

```
// app.js
App({
  onLaunch() {
    wx.cloud.init({
      env: "<云开发环境ID>", // 替换为你的环境 ID
    });
  },
});
```

初始化成功后，即可通过 `wx.cloud.extend.AI` 调用 AI 能力。

## [#](#第-2-步：调用大模型生成文本) 第 2 步：调用大模型生成文本

### [#](#流式调用（推荐）) 流式调用（推荐）

流式调用可以边生成边显示，用户体验更好：

```
const model = wx.cloud.extend.AI.createModel("cloudbase");

const res = await model.streamText({
  data: {
    model: "hy3-preview",
    messages: [{ role: "user", content: "你好，介绍一下你自己" }],
  },
});

// 逐字接收生成的文本
for await (const text of res.textStream) {
  console.log(text);
}
```

### [#](#非流式调用) 非流式调用

一次性返回完整结果，适用于短文本：

```
const model = wx.cloud.extend.AI.createModel("cloudbase");

const res = await model.generateText({
  model: "hy3-preview",
  messages: [{ role: "user", content: "你好" }],
});

console.log(res.choices[0].message.content);
```

## [#](#第-3-步：在页面中展示对话) 第 3 步：在页面中展示对话

一个最简单的聊天页面示例：

**chat.js：**

```
Page({
  data: {
    messages: [],
    inputValue: "",
    isLoading: false,
  },

  async sendMessage() {
    const { inputValue, messages } = this.data;
    if (!inputValue.trim() || this.data.isLoading) return;

    const userMessage = { role: "user", content: inputValue };
    const newMessages = [...messages, userMessage];

    this.setData({
      messages: [...newMessages, { role: "assistant", content: "" }],
      inputValue: "",
      isLoading: true,
    });

    try {
      const model = wx.cloud.extend.AI.createModel("cloudbase");
      let assistantContent = "";

      const res = await model.streamText({
        data: {
          model: "hy3-preview",
          messages: newMessages,
        },
      });

      for await (const text of res.textStream) {
        assistantContent += text;
        this.setData({
          messages: [
            ...newMessages,
            { role: "assistant", content: assistantContent },
          ],
        });
      }
    } catch (error) {
      console.error("调用失败:", error);
      wx.showToast({ title: "请求失败", icon: "error" });
    } finally {
      this.setData({ isLoading: false });
    }
  },
});
```

Incorrect translation.