# [#](#Object-VideoDecoder-getFrameData) Object VideoDecoder.getFrameData()

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持

## [#](#功能描述) 功能描述

获取下一帧的解码数据

## [#](#返回值) 返回值

### [#](#Object) Object

视频帧数据，若取不到则返回 null。当缓冲区为空的时候可能暂停取不到数据。

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 帧数据宽度 |
| height | number | 帧数据高度 |
| data | ArrayBuffer | 帧数据 |
| pkPts | number | 帧原始 pts |
| pkDts | number | 帧原始 dts |

Incorrect translation.