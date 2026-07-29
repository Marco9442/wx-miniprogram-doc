# [#](#CanvasContext-createPattern-string-image-string-repetition) CanvasContext.createPattern(string image, string repetition)

CanvasContext 是旧版的接口，新版 [Canvas 2D](../../component/canvas.html) 接口与 Web 一致

从基础库 [2.9.0](../../framework/compatibility.html) 开始，本接口停止维护，请使用 [RenderingContext](RenderingContext.html) 代替

> 基础库 1.9.90 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：支持

> 相关文档: [旧版画布迁移指南](../../framework/ability/canvas-legacy-migration.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

对指定的图像创建模式的方法，可在指定的方向上重复元图像

## [#](#参数) 参数

### [#](#string-image) string image

重复的图像源，支持代码包路径和本地临时路径 (本地路径)

### [#](#string-repetition) string repetition

如何重复图像

**repetition 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| repeat | 水平竖直方向都重复 |  |
| repeat-x | 水平方向重复 |  |
| repeat-y | 竖直方向重复 |  |
| no-repeat | 不重复 |  |

## [#](#示例代码) 示例代码

```
    const ctx = wx.createCanvasContext('myCanvas')
    const pattern = ctx.createPattern('/path/to/image', 'repeat-x')
    ctx.fillStyle = pattern
    ctx.fillRect(0, 0, 300, 150)
    ctx.draw()
```

Incorrect translation.