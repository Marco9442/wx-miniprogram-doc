# [#](#BLEPeripheralServer-offCharacteristicUnsubscribed-function-listener) BLEPeripheralServer.offCharacteristicUnsubscribed(function listener)

> 基础库 2.13.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

> 相关文档: [蓝牙介绍](../../../framework/device/bluetooth.html)

## [#](#功能描述) 功能描述

移除取消特征订阅事件的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onCharacteristicUnsubscribed 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
const listener = function (res) { console.log(res) }

BLEPeripheralServer.onCharacteristicUnsubscribed(listener)
BLEPeripheralServer.offCharacteristicUnsubscribed(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.