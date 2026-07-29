# [#](#wx-compressVideo-Object-object) wx.compressVideo(Object object)

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.11.1](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

压缩视频接口。开发者可指定压缩质量 `quality` 进行压缩。当需要更精细的控制时，可指定 `bitrate`、`fps`、和 `resolution`，当 `quality` 传入时，这三个参数将被忽略。原视频的相关信息可通过 [getVideoInfo](wx.getVideoInfo.html) 获取。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | src | string |  | 是 | 视频文件路径，可以是临时文件路径也可以是永久文件路径 |
|  | quality | string |  | 否 | 压缩质量 |
|  | | 合法值 | 说明 | | --- | --- | | low | 低 | | medium | 中 | | high | 高 | | | | | |
|  | bitrate | number |  | 是 | 码率，单位 kbps |
|  | fps | number |  | 是 | 帧率 |
|  | resolution | number |  | 是 | 相对于原视频的分辨率比例，取值范围(0, 1] |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| tempFilePath | string | 压缩后的临时文件地址 |
| size | number | 压缩后的大小，单位 kB |

Incorrect translation.