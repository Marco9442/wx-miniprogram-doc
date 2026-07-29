# [#](#Path2D) Path2D

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> 相关文档: [画布指南](../../framework/ability/canvas.html)、[canvas 组件介绍](../../component/canvas.html)

Canvas 2D API 的接口 Path2D 用来声明路径，此路径稍后会被CanvasRenderingContext2D 对象使用。CanvasRenderingContext2D 接口的 路径方法 也存在于 Path2D 这个接口中，允许你在 canvas 中根据需要创建可以保留并重用的路径。

## [#](#方法) 方法

### [#](#Path2D-addPath-Path2D-path) [Path2D.addPath(Path2D path)](Path2D.addPath.html)

添加路径到当前路径。

### [#](#Path2D-arc-number-x-number-y-number-radius-number-startAngle-number-endAngle-boolean-counterclockwise) [Path2D.arc(number x, number y, number radius, number startAngle, number endAngle, boolean counterclockwise)](Path2D.arc.html)

添加一段圆弧路径。

### [#](#Path2D-arcTo-number-x1-number-y1-number-x2-number-y2-number-radius) [Path2D.arcTo(number x1, number y1, number x2, number y2, number radius)](Path2D.arcTo.html)

通过给定控制点添加一段圆弧路径。

### [#](#Path2D-bezierCurveTo-number-cp1x-number-cp1y-number-cp2x-number-cp2y-number-x-number-y) [Path2D.bezierCurveTo(number cp1x, number cp1y, number cp2x, number cp2y, number x, number y)](Path2D.bezierCurveTo.html)

添加三次贝塞尔曲线路径。

### [#](#Path2D-closePath) [Path2D.closePath()](Path2D.closePath.html)

闭合路径到起点。

### [#](#Path2D-ellipse-number-x-number-y-number-radiusX-number-radiusY-number-rotation-number-startAngle-number-endAngle-boolean-counterclockwise) [Path2D.ellipse(number x, number y, number radiusX, number radiusY, number rotation, number startAngle, number endAngle, boolean counterclockwise)](Path2D.ellipse.html)

添加椭圆弧路径

### [#](#Path2D-lineTo-number-x-number-y) [Path2D.lineTo(number x, number y)](Path2D.lineTo.html)

添加直线路径

### [#](#Path2D-moveTo-number-x-number-y) [Path2D.moveTo(number x, number y)](Path2D.moveTo.html)

移动路径开始点

### [#](#Path2D-quadraticCurveTo-number-cpx-number-cpy-number-x-number-y) [Path2D.quadraticCurveTo(number cpx, number cpy, number x, number y)](Path2D.quadraticCurveTo.html)

添加二次贝塞尔曲线路径。

### [#](#Path2D-rect-number-x-number-y-number-width-number-height) [Path2D.rect(number x, number y, number width, number height)](Path2D.rect.html)

添加方形路径。

Incorrect translation.