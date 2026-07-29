# [#](#wx-offBLEMTUChange-function-listener) wx.offBLEMTUChange(function listener)

> 基础库 2.20.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.20.1](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [蓝牙低功耗 (BLE)](../../../framework/device/ble.html)

## [#](#功能描述) 功能描述

移除蓝牙低功耗的最大传输单元变化事件的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onBLEMTUChange 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
const listener = function (res) { console.log(res) }

wx.onBLEMTUChange(listener)
wx.offBLEMTUChange(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.