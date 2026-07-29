# [#](#Object-VKFrame-getDepthBuffer) Object VKFrame.getDepthBuffer()

> 基础库 3.0.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

获取每帧的深度图信息Buffer。安卓微信 8.0.38 开始支持，iOS微信 8.0.39 开始支持。

## [#](#返回值) 返回值

### [#](#Object) Object

帧深度纹理buffer对象

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 深度纹理宽 |
| height | number | 深度纹理高 |
| DepthAddress | ArrayBuffer | 深度纹理buffer |

Incorrect translation.