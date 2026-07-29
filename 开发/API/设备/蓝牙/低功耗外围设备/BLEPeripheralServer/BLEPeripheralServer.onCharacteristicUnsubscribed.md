# [#](#BLEPeripheralServer-onCharacteristicUnsubscribed-function-listener) BLEPeripheralServer.onCharacteristicUnsubscribed(function listener)

> 基础库 2.13.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

> 相关文档: [蓝牙介绍](../../../framework/device/bluetooth.html)

## [#](#功能描述) 功能描述

监听取消特征订阅事件，仅 iOS 支持。

## [#](#参数) 参数

### [#](#function-listener) function listener

取消特征订阅事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| serviceId | String | 蓝牙特征对应服务的 UUID |
| characteristicId | String | 蓝牙特征的 UUID |

Incorrect translation.