# [#](#Image-OffscreenCanvas-createImage) [Image](Image.html) OffscreenCanvas.createImage()

> 基础库 2.7.3 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.16.1](../../framework/compatibility.html)

> 相关文档: [画布指南](../../framework/ability/canvas.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

创建一个图片对象。支持在 2D Canvas 和 WebGL Canvas 下使用, 但不支持混用 2D 和 WebGL 的方法。

## [#](#返回值) 返回值

### [#](#Image) [Image](Image.html)

注意不允许混用 webgl 和 2d 画布创建的图片对象，使用时请注意尽量使用 canvas 自身的 `createImage` 创建图片对象。

Incorrect translation.