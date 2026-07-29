# [#](#CanvasContext-clearRect-number-x-number-y-number-width-number-height) CanvasContext.clearRect(number x, number y, number width, number height)

CanvasContext 是旧版的接口，新版 [Canvas 2D](../../component/canvas.html) 接口与 Web 一致

从基础库 [2.9.0](../../framework/compatibility.html) 开始，本接口停止维护，请使用 [RenderingContext](RenderingContext.html) 代替

> **小程序插件**：支持

> 相关文档: [旧版画布迁移指南](../../framework/ability/canvas-legacy-migration.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

清除画布上在该矩形区域内的内容

## [#](#参数) 参数

### [#](#number-x) number x

矩形路径左上角的横坐标

### [#](#number-y) number y

矩形路径左上角的纵坐标

### [#](#number-width) number width

矩形路径的宽度

### [#](#number-height) number height

矩形路径的高度

## [#](#示例代码) 示例代码

clearRect 并非画一个白色的矩形在地址区域，而是清空，为了有直观感受，对 canvas 加了一层背景色。

```
<canvas canvas-id="myCanvas" style="border: 1px solid; background: #123456;"/>
```

```
const ctx = wx.createCanvasContext('myCanvas')
ctx.setFillStyle('red')
ctx.fillRect(0, 0, 150, 200)
ctx.setFillStyle('blue')
ctx.fillRect(150, 0, 150, 200)
ctx.clearRect(10, 10, 150, 75)
ctx.draw()
```

![](data:image/png;base64,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)

Incorrect translation.