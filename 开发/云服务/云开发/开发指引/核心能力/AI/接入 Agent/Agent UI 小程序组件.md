# [#](#Agent-UI-小程序组件) Agent UI 小程序组件

`Agent UI` 是一个小程序源码组件，帮助开发者快速搭建聊天界面，支持对接云开发 Agent（智能体）和大模型。

`Agent UI` 提供以下功能：

- 对接云开发 Agent — 通过 `chatMode: "bot"` 使用
- 对接云开发大模型 — 通过 `chatMode: "model"` 使用
- 内置文件上传、图片上传、语音输入、联网搜索、多会话管理等能力

## [#](#快速体验) 快速体验

**方式一：** 通过微信开发者工具模板创建

打开微信开发者工具，点击新建小程序项目，在「**开发模式**」中选择「**小程序**」，「**模板**」分类中找到并选择 **Agent UI / 云开发 AI** 相关模板，创建后即可按模板指引直接运行体验。

**方式二：** 下载源码包导入

[下载项目示例源码包](https://gitee.com/TencentCloudBase/cloudbase-agent-ui/tree/main/apps/miniprogram-agent-ui)
，导入到微信开发者工具使用。

> 导入后需手动修改 `app.json` 中的 `env` 为你的环境 ID，以及 `pages/chatBot/chatBot.js` 中的 `botId` 为你的 Agent ID。

## [#](#引入组件到已有小程序) 引入组件到已有小程序

### [#](#_1-拷贝组件目录) 1. 拷贝组件目录

将 `miniprogram/components/agent-ui` 目录拷贝到你的小程序项目中。

### [#](#_2-注册组件) 2. 注册组件

在页面的 `.json` 配置文件中注册组件：

```
{
  "usingComponents": {
    "agent-ui": "/components/agent-ui/index"
  }
}
```

### [#](#_3-使用组件) 3. 使用组件

在页面的 `.wxml` 文件中使用组件：

```
<agent-ui
        agentConfig="{{agentConfig}}"
        showBotAvatar="{{showBotAvatar}}"
        chatMode="{{chatMode}}"
        modelConfig="{{modelConfig}}"
        envShareConfig="{{envShareConfig}}"
/>
```

### [#](#_4-配置参数) 4. 配置参数

在页面的 `.js` 文件中编写配置：

```
Page({
    data: {
        chatMode: "bot", // "bot" 使用 Agent，"model" 使用大模型
        showBotAvatar: true,
        agentConfig: {
            botId: "<你的 Agent ID>",
            allowWebSearch: true,
            allowUploadFile: true,
            allowPullRefresh: true,
            allowUploadImage: true,
            showToolCallDetail: true,
            allowMultiConversation: true,
            allowVoice: true,
        },
    },
});
```

### [#](#_5-初始化云开发) 5. 初始化云开发

在 `app.js` 的 `onLaunch` 中初始化：

```
App({
    onLaunch() {
        wx.cloud.init({
            env: "<云开发环境ID>",
        });
    },
});
```

## [#](#组件参数) 组件参数

### [#](#基础参数) 基础参数

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| chatMode | `"bot"` | `"model"` | `"bot"` 使用 Agent，`"model"` 使用大模型 |
| showBotAvatar | boolean | 是否在对话框左侧显示头像 |

### [#](#agentConfig（Agent-模式）) agentConfig（Agent 模式）

当 `chatMode = "bot"` 时使用：

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| botId | string | **必填**，Agent ID |
| allowWebSearch | boolean | 允许客户端选择启用联网搜索 |
| allowUploadFile | boolean | 允许上传文件 |
| allowUploadImage | boolean | 允许上传图片 |
| allowPullRefresh | boolean | 允许下拉刷新 |
| allowMultiConversation | boolean | 是否展示会话列表和创建会话按钮 |
| showToolCallDetail | boolean | 是否展示工具调用细节 |
| allowVoice | boolean | 是否展示语音输入按钮 |

### [#](#modelConfig（大模型模式）) modelConfig（大模型模式）

当 `chatMode = "model"` 时使用：

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| modelProvider | string | **必填**，大模型服务商标识，见[模型版本](#模型版本) |
| quickResponseModel | string | **必填**，具体的模型版本，见[模型版本](#模型版本) |
| logo | string | 模型头像 URL |
| welcomeMsg | string | 欢迎语 |

### [#](#envShareConfig（环境共享）) envShareConfig（环境共享）

跨小程序调用其他环境的 AI 能力时使用：

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| resourceAppid | string | 资源方小程序的 AppID |
| resourceEnv | string | 资源方的云开发环境 ID |

## [#](#使用示例) 使用示例

### [#](#使用-Agent) 使用 Agent

```
Page({
    data: {
        chatMode: "bot",
        showBotAvatar: true,
        agentConfig: {
            botId: "<你的 Agent ID>",
            allowWebSearch: true,
            allowUploadFile: true,
            allowPullRefresh: true,
            allowUploadImage: true,
            showToolCallDetail: true,
            allowMultiConversation: true,
            allowVoice: true,
        },
    },
});
```

### [#](#使用-DeepSeek-V3-模型) 使用 DeepSeek V3 模型

```
Page({
    data: {
        chatMode: "model",
        showBotAvatar: true,
        modelConfig: {
            modelProvider: "deepseek",
            quickResponseModel: "deepseek-v3",
            logo: "",
            welcomeMsg: "你好！我是 DeepSeek，有什么可以帮你的？",
        },
    },
});
```

### [#](#使用-DeepSeek-R1-模型（深度推理）) 使用 DeepSeek R1 模型（深度推理）

```
Page({
    data: {
        chatMode: "model",
        showBotAvatar: true,
        modelConfig: {
            modelProvider: "deepseek",
            quickResponseModel: "deepseek-r1",
            logo: "",
            welcomeMsg: "你好！我是 DeepSeek R1 推理模型。",
        },
    },
});
```

### [#](#使用混元模型) 使用混元模型

```
Page({
    data: {
        chatMode: "model",
        showBotAvatar: true,
        modelConfig: {
            modelProvider: "hunyuan-open",
            quickResponseModel: "hunyuan-lite",
            logo: "",
            welcomeMsg: "你好！我是混元大模型。",
        },
    },
});
```

## [#](#模型版本) 模型版本

### [#](#hunyuan) hunyuan

| modelProvider | quickResponseModel | 说明 |
| --- | --- | --- |
| `hunyuan-open` | `hunyuan-lite` | 具备强大的中文创作能力，复杂语境下的逻辑推理能力 |

### [#](#deepseek) deepseek

| modelProvider | quickResponseModel | 说明 |
| --- | --- | --- |
| `deepseek` | `deepseek-v3` | 专注于自然语言处理、知识问答、内容创作等通用任务 |
| `deepseek` | `deepseek-r1` | 推理模型，专为数学、代码生成和复杂逻辑推理任务设计 |

> Agent UI 组件中的 `modelProvider` 和 `quickResponseModel` 与 `ai.createModel()` 中的模型标识不同。
> `createModel("cloudbase")` 是 API 调用时使用的统一标识，而 Agent UI 组件需要分别指定 `modelProvider`（厂商）和
> `quickResponseModel`（模型版本）。

## [#](#功能说明) 功能说明

### [#](#文件上传) 文件上传

- **大小限制：** 单文件不超过 10MB
- **数量限制：** 单次最多 5 个文件
- **文件类型：** pdf、txt、doc、docx、ppt、pptx、xls、xlsx、csv
- **域名配置：** 需要在[微信公众平台](https://mp.weixin.qq.com)中将 `https://{envid}.api.tcloudbasegateway.com` 添加到
  request 合法域名列表（将 `{envid}` 替换为你的环境 ID）

### [#](#图片上传) 图片上传

- 每次仅支持上传单张图片，最大不超过 30MB

### [#](#语音功能) 语音功能

- 需要授予小程序麦克风权限，组件会自动发起权限申请

## [#](#通过环境共享调用其他环境的-AI-能力) 通过环境共享调用其他环境的 AI 能力

如果 A 小程序开通了云开发环境，B 小程序想跨环境调用 A 小程序的 AI 能力：

### [#](#前提条件) 前提条件

- A 和 B 小程序必须是**同一个主体**
- A 小程序已开通环境共享，并将环境共享给 B 小程序

登录 A 小程序，在云开发控制台开通环境共享，将环境共享给 B 小程序使用：

![](https://res8.wxqcloud.qq.com.cn/wxdoc/0a4ef13d-ba7b-4035-a5bb-b2d6a5ae03a6.png)

### [#](#配置方式) 配置方式

在 B 小程序中使用 Agent UI 时，通过 `envShareConfig` 传入 A 小程序的信息：

```
Page({
    data: {
        chatMode: "model",
        showBotAvatar: true,
        modelConfig: {
            modelProvider: "deepseek",
            quickResponseModel: "deepseek-v3",
            logo: "",
            welcomeMsg: "欢迎使用",
        },
        envShareConfig: {
            resourceAppid: "wx7a******5f4f", // A 小程序的 AppID
            resourceEnv: "chr**************46d2d", // A 小程序的环境 ID
        },
    },
});
```

> 不使用环境共享时，不要传 `envShareConfig` 参数，或将其设为 `null`。

## [#](#获取-Agent-ID) 获取 Agent ID

在 [云开发控制台 → AI → Agent](https://tcb.cloud.tencent.com/dev#/ai?tab=agent) 中创建 Agent 后，可以获取对应的 Agent ID：

![](https://res8.wxqcloud.qq.com.cn/wxdoc/527bff19-9e77-4b97-91dc-e3e8eec1e0e2.png)

Incorrect translation.