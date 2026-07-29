# [#](#SocketTask-onClose-function-listener) SocketTask.onClose(function listener)

> **小程序插件**：支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)、[局域网通信](../../../framework/ability/mDNS.html)

## [#](#功能描述) 功能描述

监听 WebSocket 连接关闭事件

## [#](#参数) 参数

### [#](#function-listener) function listener

WebSocket 连接关闭事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| code | number | 一个数字值表示关闭连接的状态号，表示连接被关闭的原因。 |
| reason | string | 一个可读的字符串，表示连接被关闭的原因。 |

Incorrect translation.