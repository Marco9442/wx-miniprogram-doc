# [#](#UploadTask-onProgressUpdate-function-listener) UploadTask.onProgressUpdate(function listener)

> 基础库 1.4.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)、[局域网通信](../../../framework/ability/mDNS.html)

## [#](#功能描述) 功能描述

监听上传进度变化事件

## [#](#参数) 参数

### [#](#function-listener) function listener

上传进度变化事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| progress | number | 上传进度百分比 |
| totalBytesSent | number | 已经上传的数据长度，单位 Bytes |
| totalBytesExpectedToSend | number | 预期需要上传的数据总长度，单位 Bytes |

Incorrect translation.