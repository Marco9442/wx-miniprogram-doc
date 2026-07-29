# [#](#UDPSocket-offListening-function-listener) UDPSocket.offListening(function listener)

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.11.1](../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)、[局域网通信](../../../framework/ability/mDNS.html)

## [#](#功能描述) 功能描述

移除开始监听数据包消息的事件的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onListening 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
const listener = function (res) { console.log(res) }

UDPSocket.onListening(listener)
UDPSocket.offListening(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.