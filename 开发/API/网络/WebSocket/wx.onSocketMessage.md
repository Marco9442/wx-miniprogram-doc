# [#](#wx-onSocketMessage-function-listener) wx.onSocketMessage(function listener)

推荐使用 [SocketTask](SocketTask.html) 的方式去管理 webSocket 链接，每一条链路的生命周期都更加可控，同时存在多个 webSocket 的链接的情况下使用 wx 前缀的方法可能会带来一些和预期不一致的情况。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)、[局域网通信](../../../framework/ability/mDNS.html)

## [#](#功能描述) 功能描述

监听 WebSocket 接收到服务器的消息事件。

## [#](#参数) 参数

### [#](#function-listener) function listener

WebSocket 接收到服务器的消息事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| data | string/ArrayBuffer | 服务器返回的消息 |

Incorrect translation.