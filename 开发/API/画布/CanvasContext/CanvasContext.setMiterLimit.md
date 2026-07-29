# [#](#CanvasContext-setMiterLimit-number-miterLimit) CanvasContext.setMiterLimit(number miterLimit)

CanvasContext 是旧版的接口，新版 [Canvas 2D](../../component/canvas.html) 接口与 Web 一致

从基础库 [1.9.90](../../framework/compatibility.html) 开始，本接口停止维护，请使用 [CanvasContext.miterLimit](CanvasContext.html) 代替

> **小程序插件**：支持

> 相关文档: [旧版画布迁移指南](../../framework/ability/canvas-legacy-migration.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

设置最大斜接长度。斜接长度指的是在两条线交汇处内角和外角之间的距离。当 [CanvasContext.setLineJoin()](CanvasContext.setLineJoin.html) 为 miter 时才有效。超过最大倾斜长度的，连接处将以 lineJoin 为 bevel 来显示。

## [#](#参数) 参数

### [#](#number-miterLimit) number miterLimit

最大斜接长度

## [#](#示例代码) 示例代码

```
const ctx = wx.createCanvasContext('myCanvas')
ctx.beginPath()
ctx.setLineWidth(10)
ctx.setLineJoin('miter')
ctx.setMiterLimit(1)
ctx.moveTo(10, 10)
ctx.lineTo(100, 50)
ctx.lineTo(10, 90)
ctx.stroke()

ctx.beginPath()
ctx.setLineWidth(10)
ctx.setLineJoin('miter')
ctx.setMiterLimit(2)
ctx.moveTo(50, 10)
ctx.lineTo(140, 50)
ctx.lineTo(50, 90)
ctx.stroke()

ctx.beginPath()
ctx.setLineWidth(10)
ctx.setLineJoin('miter')
ctx.setMiterLimit(3)
ctx.moveTo(90, 10)
ctx.lineTo(180, 50)
ctx.lineTo(90, 90)
ctx.stroke()

ctx.beginPath()
ctx.setLineWidth(10)
ctx.setLineJoin('miter')
ctx.setMiterLimit(4)
ctx.moveTo(130, 10)
ctx.lineTo(220, 50)
ctx.lineTo(130, 90)
ctx.stroke()

ctx.draw()
```

![](data:image/png;base64,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)

Incorrect translation.