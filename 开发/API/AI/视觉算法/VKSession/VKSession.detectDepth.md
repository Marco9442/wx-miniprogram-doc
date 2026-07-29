# [#](#VKSession-detectDepth-Object-object) VKSession.detectDepth(Object object)

> 基础库 2.33.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.33.0](../../../framework/compatibility.html)

## [#](#功能描述) 功能描述

深度识别。当 wx.createVKSession 参数传入 {track: {depth: {mode: 2} } } 时可用。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/depth.html)。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| frameBuffer | ArrayBuffer |  | 是 | 需要识别深度的图像像素点数据，每四项表示一个像素点的 RGBA |
| width | number |  | 是 | 图像宽度 |
| height | number |  | 是 | 图像高度 |

Incorrect translation.