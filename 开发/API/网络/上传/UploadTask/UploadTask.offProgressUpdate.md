# [#](#UploadTask-offProgressUpdate-function-listener) UploadTask.offProgressUpdate(function listener)

> 基础库 2.1.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)、[局域网通信](../../../framework/ability/mDNS.html)

## [#](#功能描述) 功能描述

移除上传进度变化事件的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onProgressUpdate 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
const listener = function (res) { console.log(res) }

UploadTask.onProgressUpdate(listener)
UploadTask.offProgressUpdate(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.