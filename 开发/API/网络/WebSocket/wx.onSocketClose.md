网络/WebSocket/wx.onSocketClose/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.onSocketClose.html\#wx-onSocketClose-function-listener) wx.onSocketClose(function listener)
推荐使用 [SocketTask](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/SocketTask.html) 的方式去管理 webSocket 链接，每一条链路的生命周期都更加可控，同时存在多个 webSocket 的链接的情况下使用 wx 前缀的方法可能会带来一些和预期不一致的情况。
> \*\*小程序插件\*\*：不支持
>
> \*\*微信 Windows 版\*\*：支持
>
> \*\*微信 Mac 版\*\*：支持
>
> \*\*微信 鸿蒙 OS 版\*\*：支持
> 相关文档: [网络使用说明](https://developers.weixin.qq.com/miniprogram/dev/framework/ability/network.html)、 [局域网通信](https://developers.weixin.qq.com/miniprogram/dev/framework/ability/mDNS.html)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.onSocketClose.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
监听 WebSocket 连接关闭事件。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.onSocketClose.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.onSocketClose.html\#function-listener) function listener
WebSocket 连接关闭事件的监听函数
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.onSocketClose.html\#%E5%8F%82%E6%95%B0-2) 参数
##### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.onSocketClose.html\#Object-res) Object res
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| code | number | 一个数字值表示关闭连接的状态号，表示连接被关闭的原因。 |
| reason | string | 一个可读的字符串，表示连接被关闭的原因。 |