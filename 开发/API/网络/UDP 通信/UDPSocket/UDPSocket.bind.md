# [#](#number-UDPSocket-bind-number-port) number UDPSocket.bind(number port)

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.11.1](../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)、[局域网通信](../../../framework/ability/mDNS.html)

## [#](#功能描述) 功能描述

绑定一个系统随机分配的可用端口，或绑定一个指定的端口号

## [#](#参数) 参数

### [#](#number-port) number port

> 基础库 2.9.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

指定要绑定的端口号，不传则返回系统随机分配的可用端口

## [#](#返回值) 返回值

### [#](#number) number

绑定成功的端口号

## [#](#示例代码) 示例代码

```
  const udp = wx.createUDPSocket()
  const port = udp.bind()
```

Incorrect translation.