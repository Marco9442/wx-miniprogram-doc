# [#](#RenderingContext-OffscreenCanvas-getContext-string-contextType) [RenderingContext](RenderingContext.html) OffscreenCanvas.getContext(string contextType)

> 基础库 2.7.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.16.1](../../framework/compatibility.html)

> 相关文档: [画布指南](../../framework/ability/canvas.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

该方法返回 OffscreenCanvas 的绘图上下文

## [#](#参数) 参数

### [#](#string-contextType) string contextType

绘图上下文类型，需要与 createOffscreenCanvas 时传入的 type 一致

**contextType 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| webgl | webgl类型上下文 |  |
| 2d | 2d类型上下文 | [2.16.1](../../framework/compatibility.html) |

## [#](#返回值) 返回值

### [#](#RenderingContext) [RenderingContext](RenderingContext.html)

注意不允许混用 webgl 和 2d 绘图上下文，传入的 contextType 必须要与 `wx.createOffscreenCanvas` 传入的 type 类型一致。

Incorrect translation.