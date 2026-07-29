基础/小程序/应用级事件/wx.offUnhandledRejection/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offUnhandledRejection.html\#wx-offUnhandledRejection-function-listener) wx.offUnhandledRejection(function listener)
> 基础库 2.10.0 开始支持，低版本需做 [兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。
> \*\*小程序插件\*\*：不支持
>
> \*\*微信 鸿蒙 OS 版\*\*：支持
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offUnhandledRejection.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
移除未处理的 Promise 拒绝事件的监听函数
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offUnhandledRejection.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offUnhandledRejection.html\#function-listener) function listener
onUnhandledRejection 传入的监听函数。不传此参数则移除所有监听函数。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offUnhandledRejection.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
```js
const listener = function (res) { console.log(res) }
wx.onUnhandledRejection(listener)
wx.offUnhandledRejection(listener) // 需传入与监听时同一个的函数对象
```