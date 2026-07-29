# [#](#OffscreenCanvas) OffscreenCanvas

> 基础库 2.7.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> 相关文档: [画布指南](../../framework/ability/canvas.html)、[canvas 组件介绍](../../component/canvas.html)

离屏 canvas 实例，可通过 [wx.createOffscreenCanvas](wx.createOffscreenCanvas.html) 创建。

## [#](#属性) 属性

### [#](#number-width) number width

画布宽度

### [#](#number-height) number height

画布高度

## [#](#方法) 方法

### [#](#RenderingContext-OffscreenCanvas-getContext-string-contextType) [RenderingContext OffscreenCanvas.getContext(string contextType)](OffscreenCanvas.getContext.html)

该方法返回 OffscreenCanvas 的绘图上下文

### [#](#Image-OffscreenCanvas-createImage) [Image OffscreenCanvas.createImage()](OffscreenCanvas.createImage.html)

创建一个图片对象。支持在 2D Canvas 和 WebGL Canvas 下使用, 但不支持混用 2D 和 WebGL 的方法。

Incorrect translation.