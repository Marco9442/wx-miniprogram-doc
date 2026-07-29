基础/小程序/路由事件/wx.offBeforeAppRoute/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-route/wx.offBeforeAppRoute.html\#wx-offBeforeAppRoute-function-listener) wx.offBeforeAppRoute(function listener)
> 基础库 3.5.5 开始支持，低版本需做 [兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。
> \*\*小程序插件\*\*：支持，需要小程序基础库版本不低于 [3.5.5](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)
>
> \*\*微信 鸿蒙 OS 版\*\*：支持
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-route/wx.offBeforeAppRoute.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
移除路由事件的监听函数
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-route/wx.offBeforeAppRoute.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-route/wx.offBeforeAppRoute.html\#function-listener) function listener
onBeforeAppRoute 传入的监听函数。不传此参数则移除所有监听函数。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-route/wx.offBeforeAppRoute.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
```js
const listener = function (res) { console.log(res) }
wx.onBeforeAppRoute(listener)
wx.offBeforeAppRoute(listener) // 需传入与监听时同一个的函数对象
```