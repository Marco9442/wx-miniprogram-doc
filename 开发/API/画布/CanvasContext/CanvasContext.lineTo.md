# [#](#CanvasContext-lineTo-number-x-number-y) CanvasContext.lineTo(number x, number y)

CanvasContext 是旧版的接口，新版 [Canvas 2D](../../component/canvas.html) 接口与 Web 一致

从基础库 [2.9.0](../../framework/compatibility.html) 开始，本接口停止维护，请使用 [RenderingContext](RenderingContext.html) 代替

> **小程序插件**：支持

> 相关文档: [旧版画布迁移指南](../../framework/ability/canvas-legacy-migration.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

增加一个新点，然后创建一条从上次指定点到目标点的线。用 `stroke` 方法来画线条

## [#](#参数) 参数

### [#](#number-x) number x

目标位置的 x 坐标

### [#](#number-y) number y

目标位置的 y 坐标

## [#](#示例代码) 示例代码

```
const ctx = wx.createCanvasContext('myCanvas')
ctx.moveTo(10, 10)
ctx.rect(10, 10, 100, 50)
ctx.lineTo(110, 60)
ctx.stroke()
ctx.draw()
```

![](data:image/png;base64,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)

Incorrect translation.