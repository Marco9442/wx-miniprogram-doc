# [#](#RenderingContext-Canvas-getContext-string-contextType) [RenderingContext](RenderingContext.html) Canvas.getContext(string contextType)

> 基础库 2.7.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：支持

> 相关文档: [画布指南](../../framework/ability/canvas.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

该方法返回 Canvas 的绘图上下文

## [#](#参数) 参数

### [#](#string-contextType) string contextType

上下文类型

**contextType 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| 2d | 2d 绘图上下文 |  |
| webgl | webgl 绘图上下文 |  |
| webgl2 | webgl2 绘图上下文 | [2.24.0](../../framework/compatibility.html) |

## [#](#返回值) 返回值

### [#](#RenderingContext) [RenderingContext](RenderingContext.html)

支持获取 2D 和 WebGL 绘图上下文

Incorrect translation.