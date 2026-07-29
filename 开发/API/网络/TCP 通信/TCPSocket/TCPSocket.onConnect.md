# [#](#TCPSocket-onConnect-function-listener) TCPSocket.onConnect(function listener)

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)

## [#](#功能描述) 功能描述

监听当一个 socket 连接成功建立的时候触发该事件

## [#](#参数) 参数

### [#](#function-listener) function listener

当一个 socket 连接成功建立的时候触发该事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- |
|  | useHttpDNS | boolean | 本次连接是否使用了 HttpDNS | [3.4.0](../../../framework/compatibility.html) |
|  | exception | Object | 网络请求过程中的一些异常信息（例如：TCPSocket.connect 传了 enableHttpDNS: true，但最终未使用 HttpDNS 时，exception 就会说明未使用 HttpDNS 的原因） | [3.4.0](../../../framework/compatibility.html) |
|  | |  | 结构属性 | 类型 | 说明 | 最低版本 | | --- | --- | --- | --- | --- | |  | reasons | Array.<Object> | 异常信息 | [3.4.0](../../../framework/compatibility.html) | |  | |  | 结构属性 | 类型 | 说明 | | --- | --- | --- | --- | |  | errMsg | string | 错误原因 | |  | errno | string | 错误码 | | | | | | | | |
|  | remoteInfo | Object | 发送端地址信息（目前仅iOS和Android端支持） | [3.4.1](../../../framework/compatibility.html) |
|  | |  | 结构属性 | 类型 | 说明 | 最低版本 | | --- | --- | --- | --- | --- | |  | address | string | 发送消息的 socket 的地址 | [3.4.1](../../../framework/compatibility.html) | |  | family | string | 使用的协议族，为 IPv4 或者 IPv6 | [3.4.1](../../../framework/compatibility.html) | |  | port | number | 端口号 | [3.4.1](../../../framework/compatibility.html) | | | | |
|  | localInfo | Object | 接收端地址信息（目前仅iOS和Android端支持） | [3.4.1](../../../framework/compatibility.html) |
|  | |  | 结构属性 | 类型 | 说明 | 最低版本 | | --- | --- | --- | --- | --- | |  | address | string | 接收消息的 socket 的地址 | [3.4.1](../../../framework/compatibility.html) | |  | family | string | 使用的协议族，为 IPv4 或者 IPv6 | [3.4.1](../../../framework/compatibility.html) | |  | port | number | 端口号 | [3.4.1](../../../framework/compatibility.html) | | | | |

Incorrect translation.