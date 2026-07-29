# [#](#TCPSocket-connect-Object-options) TCPSocket.connect(Object options)

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)

## [#](#功能描述) 功能描述

在给定的套接字上启动连接

## [#](#参数) 参数

### [#](#Object-options) Object options

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| address | string |  | 是 | 套接字要连接的地址 |  |
| port | number |  | 是 | 套接字要连接的端口 |  |
| timeout | number | 2 | 否 | 套接字要连接的超时时间，默认为 2s |  |
| enableHttpDNS | boolean | false | 否 | 是否开启 HttpDNS 服务。如开启，需要同时填入 httpDNSServiceId 。 HttpDNS 用法详见 [移动解析HttpDNS](../../../framework/ability/HTTPDNS.html) | [3.4.0](../../../framework/compatibility.html) |
| httpDNSServiceId | string |  | 否 | HttpDNS 服务商 Id。 HttpDNS 用法详见 [移动解析HttpDNS](../../../framework/ability/HTTPDNS.html) | [3.4.0](../../../framework/compatibility.html) |

## [#](#示例代码) 示例代码

```
  const tcp = wx.createTCPSocket()
  tcp.connect({address: '192.168.193.2', port: 8848})
```

Incorrect translation.