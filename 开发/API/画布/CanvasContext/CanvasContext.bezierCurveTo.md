# [#](#CanvasContext-bezierCurveTo-number-cp1x-number-cp1y-number-cp2x-number-cp2y-number-x-number-y) CanvasContext.bezierCurveTo(number cp1x, number cp1y, number cp2x, number cp2y, number x, number y)

CanvasContext 是旧版的接口，新版 [Canvas 2D](../../component/canvas.html) 接口与 Web 一致

从基础库 [2.9.0](../../framework/compatibility.html) 开始，本接口停止维护，请使用 [RenderingContext](RenderingContext.html) 代替

> **小程序插件**：支持

> 相关文档: [旧版画布迁移指南](../../framework/ability/canvas-legacy-migration.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

创建三次方贝塞尔曲线路径。曲线的起始点为路径中前一个点。

## [#](#参数) 参数

### [#](#number-cp1x) number cp1x

第一个贝塞尔控制点的 x 坐标

### [#](#number-cp1y) number cp1y

第一个贝塞尔控制点的 y 坐标

### [#](#number-cp2x) number cp2x

第二个贝塞尔控制点的 x 坐标

### [#](#number-cp2y) number cp2y

第二个贝塞尔控制点的 y 坐标

### [#](#number-x) number x

结束点的 x 坐标

### [#](#number-y) number y

结束点的 y 坐标

## [#](#示例代码) 示例代码

```
const ctx = wx.createCanvasContext('myCanvas')

// Draw points
ctx.beginPath()
ctx.arc(20, 20, 2, 0, 2 * Math.PI)
ctx.setFillStyle('red')
ctx.fill()

ctx.beginPath()
ctx.arc(200, 20, 2, 0, 2 * Math.PI)
ctx.setFillStyle('lightgreen')
ctx.fill()

ctx.beginPath()
ctx.arc(20, 100, 2, 0, 2 * Math.PI)
ctx.arc(200, 100, 2, 0, 2 * Math.PI)
ctx.setFillStyle('blue')
ctx.fill()

ctx.setFillStyle('black')
ctx.setFontSize(12)

// Draw guides
ctx.beginPath()
ctx.moveTo(20, 20)
ctx.lineTo(20, 100)
ctx.lineTo(150, 75)

ctx.moveTo(200, 20)
ctx.lineTo(200, 100)
ctx.lineTo(70, 75)
ctx.setStrokeStyle('#AAAAAA')
ctx.stroke()

// Draw quadratic curve
ctx.beginPath()
ctx.moveTo(20, 20)
ctx.bezierCurveTo(20, 100, 200, 100, 200, 20)
ctx.setStrokeStyle('black')
ctx.stroke()

ctx.draw()
```

![](data:image/png;base64,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ddmhzKjSUGEJ6HJpO+64o+jb17LckF+WNLNpq1TyU2Rr166VpqYmueaaa7IhSCvRENBH1Zqbm+WPP/7IPCbklznSmhssnfw2ELv99ttl77335mpwzVOo+A3oXt6ee+4p+qxuqA35hSKbvt3Syk+Rffvtt+5K3siRI9MTpGahCVx99dXu5eLfffdd0DiQX1C8qRovtfw2EJs4caK7gfXVV19NBZFKxSOgudac33333bkMHvnlgjlRJ8jvf7h+/vlnueCCC9z5wLfffjsRRAoXh4Dm9phjjnG51pzntSG/vEj794P8NmH11ltvuf8cp59+unzxxRf+JClpmoDK57TTTnO5rccfN+Rnb3ogvyo5mTVrlhxwwAFy8cUXy8qVK+1ljhF5Efjll1/koosukgMPPFBefPFFrzohCiG/EFRraxP5tcNv6tSpcsIJJ8iFF14oH3zwQW20qZ0bgYULF8r555/vcvfYY4/l1m+1jpBf3VOw2QCQn2dOHn/8cTn88MPdlcGnnnrKsxbF8ibw5JNPypFHHin9+/eX6dOn59191f6Qn5lU/DsQ5JcwJ3pPmC6Zv/vuu8utt94qf/31V8IWKJ41gT///FNuueUWd/X23HPPlffeey/rLmpuD/nVjDDzBpBfSqS6vtt1113n7hMcMmSIPPvssylbolpaAs8884ycddZZcsQRR8gNN9yQ69XbpGNGfkmJhS+P/DJgrOJTAXbo0EGGDh0qs2fPzqBVmtgSgZdfftmdf91uu+3k7LPPlueee64QoJCfvTQhvwxzsm7dOnn00Udl8ODBsvPOO7vlkObPn59hD+Vsat68eXL55Ze7RSl0gVo9//r3338XCgbys5cu5BcoJ2vWrBFdCFPPQSlkfWBenydetGhRoB7jaVZXVlFWAwcOdOz0huQHH3zQLUpR1A352csc8sshJx9++KGMHz/eLYXes2dP6dKli7uJ+r777hN9DWLZN2Vw7733OibKRhkpKxWgsothQ372soj8cs6J7r189NFH7urkqaee6q4ad+rUyS23f9lll8nkyZPl66+/znlU+XWnsWmMGqvGrGvnKQNloUyUTZH38KqRRH75zTHfnpCfL6mA5fSViHp/2qhRo9xq0127dpXOnTu754yHDRsmd9xxh1t0QcsVZdOxvvLKK27sl1xyibs/Us+DamwDBgxwsWrMP/zwQ1FC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)

针对 moveTo(20, 20) bezierCurveTo(20, 100, 200, 100, 200, 20) 的三个关键坐标如下：

- 红色：起始点(20, 20)
- 蓝色：两个控制点(20, 100) (200, 100)
- 绿色：终止点(200, 20)

Incorrect translation.