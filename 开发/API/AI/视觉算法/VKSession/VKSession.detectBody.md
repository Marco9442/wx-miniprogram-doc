# [#](#VKSession-detectBody-Object-object) VKSession.detectBody(Object object)

> 基础库 2.28.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.28.0](../../../framework/compatibility.html)

## [#](#功能描述) 功能描述

静态图像人体关键点检测。当 wx.createVKSession 参数传入 {track: {body: {mode: 2} } } 时可用。用法详情[指南文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/visionkit/body.html)。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | frameBuffer | ArrayBuffer |  | 是 | 人脸图像像素点数据，每四项表示一个像素点的 RGBA |
|  | width | number |  | 是 | 图像宽度 |
|  | height | number |  | 是 | 图像高度 |
|  | scoreThreshold | number | 0.8 | 否 | 评分阈值。正常情况传入 0.8 即可。 |
|  | sourceType | number | 1 | 否 | 图像源类型。正常情况传入 1 即可。当输入的图片是来自一个连续视频的每一帧图像时，sourceType 传入 0 会得到更优的效果 |
|  | | 合法值 | 说明 | | --- | --- | | 1 | 表示输入的图片是随机的图片 | | 0 | 表示输入的图片是来自一个连续视频的每一帧图像 | | | | | |

Incorrect translation.