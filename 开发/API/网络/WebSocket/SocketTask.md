# [#](#SocketTask) SocketTask

> 基础库 1.7.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> 相关文档: [网络使用说明](../../../framework/ability/network.html)、[局域网通信](../../../framework/ability/mDNS.html)

WebSocket 任务，可通过 wx.connectSocket() 接口创建返回

## [#](#方法) 方法

### [#](#SocketTask-send-Object-object) [SocketTask.send(Object object)](SocketTask.send.html)

通过 WebSocket 连接发送数据

### [#](#SocketTask-close-Object-object) [SocketTask.close(Object object)](SocketTask.close.html)

关闭 WebSocket 连接

### [#](#SocketTask-onOpen-function-listener) [SocketTask.onOpen(function listener)](./SocketTask.onOpen.html)

监听 WebSocket 连接打开事件

### [#](#SocketTask-onClose-function-listener) [SocketTask.onClose(function listener)](./SocketTask.onClose.html)

监听 WebSocket 连接关闭事件

### [#](#SocketTask-onError-function-listener) [SocketTask.onError(function listener)](./SocketTask.onError.html)

监听 WebSocket 错误事件

### [#](#SocketTask-onMessage-function-listener) [SocketTask.onMessage(function listener)](./SocketTask.onMessage.html)

监听 WebSocket 接收到服务器的消息事件

Incorrect translation.