# [#](#RequestTask-onHeadersReceived-function-listener) RequestTask.onHeadersReceived(function listener)

> 基础库 2.1.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)、[局域网通信](../../../framework/ability/mDNS.html)、[移动解析HttpDNS](../../../framework/ability/HTTPDNS.html)

## [#](#功能描述) 功能描述

监听 HTTP Response Header 事件。会比请求完成事件更早

## [#](#参数) 参数

### [#](#function-listener) function listener

HTTP Response Header 事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| header | Object | 开发者服务器返回的 HTTP Response Header |
| statusCode | Number | 开发者服务器返回的 HTTP 状态码 （目前开发者工具上不会返回 statusCode 字段，可用真机查看该字段，后续将会支持） |
| cookies | Array.<string> | 开发者服务器返回的 cookies，格式为字符串数组 |

Incorrect translation.