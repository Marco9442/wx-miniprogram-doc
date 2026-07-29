画布/CanvasContext/CanvasContext.measureText/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/CanvasContext.measureText.html\#Object-CanvasContext-measureText-string-text) Object CanvasContext.measureText(string text)
CanvasContext 是旧版的接口，新版 [Canvas 2D](https://developers.weixin.qq.com/miniprogram/dev/component/canvas.html) 接口与 Web 一致
从基础库 [2.9.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) 开始，本接口停止维护，请使用 [RenderingContext](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/RenderingContext.html) 代替
> 基础库 1.9.90 开始支持，低版本需做 [兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。
> \*\*小程序插件\*\*：支持
> 相关文档: [旧版画布迁移指南](https://developers.weixin.qq.com/miniprogram/dev/framework/ability/canvas-legacy-migration.html)、 [canvas 组件介绍](https://developers.weixin.qq.com/miniprogram/dev/component/canvas.html)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/CanvasContext.measureText.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
测量文本尺寸信息。目前仅返回文本宽度。同步接口。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/CanvasContext.measureText.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/CanvasContext.measureText.html\#string-text) string text
要测量的文本
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/CanvasContext.measureText.html\#%E8%BF%94%E5%9B%9E%E5%80%BC) 返回值
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/CanvasContext.measureText.html\#Object) Object
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 文本的宽度 |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/CanvasContext.measureText.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
```javascript
const ctx = wx.createCanvasContext('myCanvas')
ctx.font = 'italic bold 20px cursive'
const metrics = ctx.measureText('Hello World')
console.log(metrics.width)
```