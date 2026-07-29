# [#](#TCPSocket) TCPSocket

> 基础库 2.18.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> 相关文档: [网络使用说明](../../../framework/ability/network.html)

一个 TCP Socket 实例，默认使用 IPv4 协议

## [#](#方法) 方法

### [#](#TCPSocket-bindWifi-Object-options) [TCPSocket.bindWifi(Object options)](TCPSocket.bindWifi.html)

将 TCP Socket 绑定到当前 wifi 网络，成功后会触发 onBindWifi 事件（仅安卓支持）

### [#](#TCPSocket-connect-Object-options) [TCPSocket.connect(Object options)](TCPSocket.connect.html)

在给定的套接字上启动连接

### [#](#TCPSocket-write-string-ArrayBuffer-data) [TCPSocket.write(string|ArrayBuffer data)](TCPSocket.write.html)

在 socket 上发送数据

### [#](#TCPSocket-close) [TCPSocket.close()](TCPSocket.close.html)

关闭连接

### [#](#TCPSocket-onClose-function-listener) [TCPSocket.onClose(function listener)](./TCPSocket.onClose.html)

监听一旦 socket 完全关闭就发出该事件

### [#](#TCPSocket-offClose-function-listener) [TCPSocket.offClose(function listener)](./TCPSocket.offClose.html)

移除一旦 socket 完全关闭就发出该事件的监听函数

### [#](#TCPSocket-onConnect-function-listener) [TCPSocket.onConnect(function listener)](./TCPSocket.onConnect.html)

监听当一个 socket 连接成功建立的时候触发该事件

### [#](#TCPSocket-offConnect-function-listener) [TCPSocket.offConnect(function listener)](./TCPSocket.offConnect.html)

移除当一个 socket 连接成功建立的时候触发该事件的监听函数

### [#](#TCPSocket-onError-function-listener) [TCPSocket.onError(function listener)](./TCPSocket.onError.html)

监听当错误发生时触发

### [#](#TCPSocket-offError-function-listener) [TCPSocket.offError(function listener)](./TCPSocket.offError.html)

移除当错误发生时触发的监听函数

### [#](#TCPSocket-onMessage-function-listener) [TCPSocket.onMessage(function listener)](./TCPSocket.onMessage.html)

监听当接收到数据的时触发该事件

### [#](#TCPSocket-offMessage-function-listener) [TCPSocket.offMessage(function listener)](./TCPSocket.offMessage.html)

移除当接收到数据的时触发该事件的监听函数

### [#](#TCPSocket-onBindWifi-function-listener) [TCPSocket.onBindWifi(function listener)](./TCPSocket.onBindWifi.html)

监听当一个 socket 绑定当前 wifi 网络成功时触发该事件

### [#](#TCPSocket-offBindWifi-function-listener) [TCPSocket.offBindWifi(function listener)](./TCPSocket.offBindWifi.html)

移除当一个 socket 绑定当前 wifi 网络成功时触发该事件的监听函数

## [#](#错误) 错误

| 错误码 | 错误信息 | 说明 |
| --- | --- | --- |
| -1 |  | 系统错误 |
| -2 |  | socket接口错误，可参考系统的socket错误码 |
| -3 |  | 发送失败，无接口权限 |
| -4 |  | 链接失败 |
| 1 |  | 发送失败，参数错误，address不合法 |
| 2 |  | 发送失败，参数错误，port不合法 |
| 3 |  | 绑定wifi网络失败，BSSID不合法 |
| 4 |  | 绑定wifi网络失败，系统错误 |
| 5 |  | 绑定wifi网络失败，该接口仅在安卓平台支持 |
| 6 |  | 绑定wifi网络失败，低版本安卓不支持该接口 |

## [#](#注意) 注意

- 当 errCode 为 -2 时，errMsg 里应该会有相应的 errno ，开发者可以根据 errno 到 linux 代码里的 [errno-base.h](https://github.com/torvalds/linux/blob/master/include/uapi/asm-generic/errno-base.h) 和 [errno.h](https://github.com/torvalds/linux/blob/master/include/uapi/asm-generic/errno.h) 中查看具体的报错信息。

Incorrect translation.