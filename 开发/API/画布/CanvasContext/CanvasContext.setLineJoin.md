# [#](#CanvasContext-setLineJoin-string-lineJoin) CanvasContext.setLineJoin(string lineJoin)

CanvasContext 是旧版的接口，新版 [Canvas 2D](../../component/canvas.html) 接口与 Web 一致

从基础库 [1.9.90](../../framework/compatibility.html) 开始，本接口停止维护，请使用 [CanvasContext.lineJoin](CanvasContext.html) 代替

> **小程序插件**：支持

> 相关文档: [旧版画布迁移指南](../../framework/ability/canvas-legacy-migration.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

设置线条的交点样式

## [#](#参数) 参数

### [#](#string-lineJoin) string lineJoin

线条的结束交点样式

**lineJoin 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| bevel | 斜角 |  |
| round | 圆角 |  |
| miter | 尖角 |  |

## [#](#示例代码) 示例代码

```
const ctx = wx.createCanvasContext('myCanvas')
ctx.beginPath()
ctx.moveTo(10, 10)
ctx.lineTo(100, 50)
ctx.lineTo(10, 90)
ctx.stroke()

ctx.beginPath()
ctx.setLineJoin('bevel')
ctx.setLineWidth(10)
ctx.moveTo(50, 10)
ctx.lineTo(140, 50)
ctx.lineTo(50, 90)
ctx.stroke()

ctx.beginPath()
ctx.setLineJoin('round')
ctx.setLineWidth(10)
ctx.moveTo(90, 10)
ctx.lineTo(180, 50)
ctx.lineTo(90, 90)
ctx.stroke()

ctx.beginPath()
ctx.setLineJoin('miter')
ctx.setLineWidth(10)
ctx.moveTo(130, 10)
ctx.lineTo(220, 50)
ctx.lineTo(130, 90)
ctx.stroke()

ctx.draw()
```

![](data:image/png;base64,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)

Incorrect translation.