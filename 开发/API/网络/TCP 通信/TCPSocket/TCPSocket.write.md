# [#](#TCPSocket-write-string-ArrayBuffer-data) TCPSocket.write(string|ArrayBuffer data)

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)

## [#](#功能描述) 功能描述

在 socket 上发送数据

## [#](#参数) 参数

### [#](#string-ArrayBuffer-data) string|ArrayBuffer data

要发送的数据

## [#](#示例代码) 示例代码

```
  const tcp = wx.createTCPSocket()
  tcp.write('hello, how are you')
```

Incorrect translation.