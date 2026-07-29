# [#](#Object-VKFrame-getLegSegmentBuffer) Object VKFrame.getLegSegmentBuffer()

> 基础库 3.2.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

获取每帧的腿部分割信息Buffer，安卓微信 8.0.43，iOS微信 8.0.43 开始支持。

## [#](#返回值) 返回值

### [#](#Object) Object

帧深度纹理buffer对象，width \* height 大小的 深度值（float32）

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 腿部分割纹理宽 |
| height | number | 腿部分割纹理高 |
| DepthAddress | ArrayBuffer | 腿部分割纹理buffer，width \* height 大小的 裁剪值（0 为不是脚，越靠近 255 越接近腿部区域）（uint8） |

Incorrect translation.