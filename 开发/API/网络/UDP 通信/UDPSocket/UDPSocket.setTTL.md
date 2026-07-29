# [#](#UDPSocket-setTTL-number-ttl) UDPSocket.setTTL(number ttl)

> 基础库 2.18.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)、[局域网通信](../../../framework/ability/mDNS.html)

## [#](#功能描述) 功能描述

设置 IP\_TTL 套接字选项，用于设置一个 IP 数据包传输时允许的最大跳步数

## [#](#参数) 参数

### [#](#number-ttl) number ttl

ttl 参数可以是 0 到 255 之间

## [#](#示例代码) 示例代码

```
  const udp = wx.createUDPSocket()
  udp.onListening(function () {
    udp.setTTL(64)
  })
  udp.bind()
```

Incorrect translation.