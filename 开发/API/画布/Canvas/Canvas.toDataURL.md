# [#](#string-Canvas-toDataURL-string-type-number-encoderOptions) string Canvas.toDataURL(string type, number encoderOptions)

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：支持

> 相关文档: [画布指南](../../framework/ability/canvas.html)、[canvas 组件介绍](../../component/canvas.html)

## [#](#功能描述) 功能描述

返回一个包含图片展示的 data URI 。可以使用 type 参数其类型，默认为 PNG 格式。

## [#](#参数) 参数

### [#](#string-type) string type

图片格式，默认为 image/png

### [#](#number-encoderOptions) number encoderOptions

在指定图片格式为 image/jpeg 或 image/webp的情况下，可以从 0 到 1 的区间内选择图片的质量。如果超出取值范围，将会使用默认值 0.92。其他参数会被忽略。

## [#](#返回值) 返回值

### [#](#string) string

Incorrect translation.