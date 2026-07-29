# [#](#RequestTask-onChunkReceived-function-listener) RequestTask.onChunkReceived(function listener)

> 基础库 2.20.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)、[局域网通信](../../../framework/ability/mDNS.html)、[移动解析HttpDNS](../../../framework/ability/HTTPDNS.html)

## [#](#功能描述) 功能描述

监听 Transfer-Encoding Chunk Received 事件。当接收到新的chunk时触发。

## [#](#参数) 参数

### [#](#function-listener) function listener

Transfer-Encoding Chunk Received 事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| data | ArrayBuffer | 返回的chunk buffer |

Incorrect translation.