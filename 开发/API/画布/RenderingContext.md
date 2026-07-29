# [#](#RenderingContext) RenderingContext

> 相关文档: [画布指南](../../framework/ability/canvas.html)、[canvas 组件介绍](../../component/canvas.html)

Canvas 绘图上下文。

- 通过 Canvas.getContext('2d') 接口可以获取 CanvasRenderingContext2D 对象，实现了 [HTML Canvas 2D Context](https://www.w3.org/TR/2dcontext/) 定义的属性、方法。
- 通过 Canvas.getContext('webgl') 或 OffscreenCanvas.getContext('webgl') 接口可以获取 WebGLRenderingContext 对象，实现了 [WebGL 1.0](https://www.khronos.org/registry/webgl/specs/latest/1.0/) 定义的所有属性、方法、常量。
- CanvasRenderingContext2D 的 drawImage 方法 2.10.0 起支持传入通过 [SelectorQuery](../wxml/SelectorQuery.html) 获取的 video 对象，2.29.0 起支持传入开启了自定义渲染的 [LivePusherContext](../media/live/LivePusherContext.html) 对象。

## [#](#示例代码) 示例代码

video 画到 2D Canvas 示例
[在开发者工具中预览效果](https://developers.weixin.qq.com/s/tJTak7mU7sfX "在开发者工具中预览效果")

Incorrect translation.