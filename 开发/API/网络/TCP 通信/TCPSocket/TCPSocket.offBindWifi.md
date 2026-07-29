# [#](#TCPSocket-offBindWifi-function-listener) TCPSocket.offBindWifi(function listener)

> 基础库 2.25.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [网络使用说明](../../../framework/ability/network.html)

## [#](#功能描述) 功能描述

移除当一个 socket 绑定当前 wifi 网络成功时触发该事件的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onBindWifi 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
const listener = function (res) { console.log(res) }

TCPSocket.onBindWifi(listener)
TCPSocket.offBindWifi(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.