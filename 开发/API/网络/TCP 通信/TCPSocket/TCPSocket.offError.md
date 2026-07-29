# [#](#TCPSocket-offError-function-listener) TCPSocket.offError(function listener)

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)

## [#](#功能描述) 功能描述

移除当错误发生时触发的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onError 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
const listener = function (res) { console.log(res) }

TCPSocket.onError(listener)
TCPSocket.offError(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.