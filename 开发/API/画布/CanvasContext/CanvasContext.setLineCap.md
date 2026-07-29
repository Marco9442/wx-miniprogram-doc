# [#](#CanvasContext-setLineCap-string-lineCap) CanvasContext.setLineCap(string lineCap)

CanvasContext 是旧版的接口，新版 [Canvas 2D](../../component/canvas.html) 接口与 Web 一致

从基础库 [1.9.90](../../framework/compatibility.html) 开始，本接口停止维护，请使用 [CanvasContext.lineCap](CanvasContext.html) 代替

> **小程序插件**：支持

> 相关文档: [旧版画布迁移指南](../../framework/ability/canvas-legacy-migration.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

设置线条的端点样式

## [#](#参数) 参数

### [#](#string-lineCap) string lineCap

线条的结束端点样式

**lineCap 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| butt | 向线条的每个末端添加平直的边缘。 |  |
| round | 向线条的每个末端添加圆形线帽。 |  |
| square | 向线条的每个末端添加正方形线帽。 |  |

## [#](#示例代码) 示例代码

```
const ctx = wx.createCanvasContext('myCanvas')
ctx.beginPath()
ctx.moveTo(10, 10)
ctx.lineTo(150, 10)
ctx.stroke()

ctx.beginPath()
ctx.setLineCap('butt')
ctx.setLineWidth(10)
ctx.moveTo(10, 30)
ctx.lineTo(150, 30)
ctx.stroke()

ctx.beginPath()
ctx.setLineCap('round')
ctx.setLineWidth(10)
ctx.moveTo(10, 50)
ctx.lineTo(150, 50)
ctx.stroke()

ctx.beginPath()
ctx.setLineCap('square')
ctx.setLineWidth(10)
ctx.moveTo(10, 70)
ctx.lineTo(150, 70)
ctx.stroke()

ctx.draw()
```

![](data:image/png;base64,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)

Incorrect translation.