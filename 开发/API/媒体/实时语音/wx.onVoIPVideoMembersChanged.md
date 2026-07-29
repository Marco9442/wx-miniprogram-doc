# [#](#wx-onVoIPVideoMembersChanged-function-listener) wx.onVoIPVideoMembersChanged(function listener)

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持

## [#](#功能描述) 功能描述

监听实时语音通话成员视频状态变化事件。

## [#](#参数) 参数

### [#](#function-listener) function listener

实时语音通话成员视频状态变化事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| openIdList | Array.<String> | 开启视频的成员名单 |
| errCode | Number | 错误码 |
| errMsg | String | 调用结果 |

Incorrect translation.