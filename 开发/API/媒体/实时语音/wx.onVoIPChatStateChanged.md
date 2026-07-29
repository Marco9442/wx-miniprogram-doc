# [#](#wx-onVoIPChatStateChanged-function-listener) wx.onVoIPChatStateChanged(function listener)

> 基础库 2.16.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持

> 相关文档: [多人音视频对话](../../../framework/open-ability/voip-chat.html)

## [#](#功能描述) 功能描述

监听房间状态变化事件。

## [#](#参数) 参数

### [#](#function-listener) function listener

房间状态变化事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| code | Number | 事件码 |
| data | object | 附加信息 |
| errCode | Number | 错误码 |
| errMsg | String | 调用结果 |

Incorrect translation.