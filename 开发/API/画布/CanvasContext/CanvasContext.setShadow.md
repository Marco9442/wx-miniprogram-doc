# [#](#CanvasContext-setShadow-number-offsetX-number-offsetY-number-blur-string-color) CanvasContext.setShadow(number offsetX, number offsetY, number blur, string color)

CanvasContext 是旧版的接口，新版 [Canvas 2D](../../component/canvas.html) 接口与 Web 一致

从基础库 [1.9.90](../../framework/compatibility.html) 开始，本接口停止维护，请使用 [CanvasContext.shadowOffsetX|CanvasContext.shadowOffsetY|CanvasContext.shadowColor|CanvasContext.shadowBlur](CanvasContext.html) 代替

> **小程序插件**：支持

> 相关文档: [旧版画布迁移指南](../../framework/ability/canvas-legacy-migration.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

设定阴影样式。

## [#](#参数) 参数

### [#](#number-offsetX) number offsetX

阴影相对于形状在水平方向的偏移，默认值为 0。

### [#](#number-offsetY) number offsetY

阴影相对于形状在竖直方向的偏移，默认值为 0。

### [#](#number-blur) number blur

阴影的模糊级别，数值越大越模糊。范围 0- 100。，默认值为 0。

### [#](#string-color) string color

阴影的颜色。默认值为 black。

## [#](#示例代码) 示例代码

```
const ctx = wx.createCanvasContext('myCanvas')
ctx.setFillStyle('red')
ctx.setShadow(10, 50, 50, 'blue')
ctx.fillRect(10, 10, 150, 75)
ctx.draw()
```

![](https://res.wx.qq.com/wxdoc/dist/assets/img/shadow.744997d7.png)

Incorrect translation.