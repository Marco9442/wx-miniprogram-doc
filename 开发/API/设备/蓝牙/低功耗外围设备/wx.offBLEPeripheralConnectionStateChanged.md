# [#](#wx-offBLEPeripheralConnectionStateChanged-function-listener) wx.offBLEPeripheralConnectionStateChanged(function listener)

> 基础库 2.10.3 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.22.1](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

移除当前外围设备被连接或断开连接事件的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onBLEPeripheralConnectionStateChanged 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
const listener = function (res) { console.log(res) }

wx.onBLEPeripheralConnectionStateChanged(listener)
wx.offBLEPeripheralConnectionStateChanged(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.