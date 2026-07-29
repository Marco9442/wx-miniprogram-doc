基础/性能/wx.preloadAssets/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/performance/wx.preloadAssets.html\#wx-preloadAssets-Object-object) wx.preloadAssets(Object object)
> 基础库 2.22.1 开始支持，低版本需做 [兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。
> \*\*以 [Promise 风格](https://developers.weixin.qq.com/miniprogram/dev/framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用\*\*：不支持
>
> \*\*小程序插件\*\*：不支持
>
> \*\*微信 Windows 版\*\*：支持
>
> \*\*微信 Mac 版\*\*：支持
>
> \*\*微信 鸿蒙 OS 版\*\*：支持
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/performance/wx.preloadAssets.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
为视图层预加载媒体资源文件, 目前支持：font，image
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/performance/wx.preloadAssets.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/performance/wx.preloadAssets.html\#Object-object) Object object
| | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
| | data | Array. | | 是 | |
| | | | 结构属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
| | type | string | | 是 | |
| | | 合法值 | 说明 |
| --- | --- |
| 'font' | 字体 |
| 'image' | 图片 | |
| | src | string | | 是 | | |
| | success | function | | 否 | 接口调用成功的回调函数 |
| | fail | function | | 否 | 接口调用失败的回调函数 |
| | complete | function | | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/performance/wx.preloadAssets.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
```js
wx.preloadAssets({
data: [\
{\
type: 'image',\
src: imgUrl,\
},\
],
success(resp) {
console.log('preloadAssets success', resp)
},
fail(err) {
console.log('preloadAssets fail', err)
},
})
```
- 开发过程中，可在开发者工具network面板查看预加载情况。