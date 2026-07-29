# [#](#TCPSocket-wx-createTCPSocket-Object-object) [TCPSocket](TCPSocket.html) wx.createTCPSocket(Object object)

> 基础库 2.18.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)

## [#](#功能描述) 功能描述

创建一个 TCP Socket 实例。使用前请注意阅读[相关说明](../../../framework/ability/network.html)。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | type | string | ipv4 | 否 | 套接字族，必须是 IPv4 或者 IPv6，默认是 IPv4 | [3.6.4](../../../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | ipv4 | IPv4 | | ipv6 | IPv6 | | | | | | |

## [#](#返回值) 返回值

### [#](#TCPSocket) [TCPSocket](TCPSocket.html)

一个 TCP Socket 实例

## [#](#连接限制) 连接限制

- 允许与局域网内的非本机 IP 通信
- 允许与配置过的服务器域名通信，详见[相关说明](../../../framework/ability/network.html)
- 禁止与以下端口号连接：`1024 以下` `1099` `1433` `1521` `1719` `1720` `1723` `2049` `2375` `3128` `3306` `3389` `3659` `4045` `5060` `5061` `5432` `5984` `6379` `6000` `6566` `7001` `7002` `8000-8100` `8443` `8888` `9200` `9300` `10051` `10080` `11211` `27017` `27018` `27019`
- 每 5 分钟内最多创建 20 个 TCPSocket

Incorrect translation.