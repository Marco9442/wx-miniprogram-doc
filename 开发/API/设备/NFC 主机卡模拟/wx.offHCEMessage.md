# [#](#wx-offHCEMessage-function-listener) wx.offHCEMessage(function listener)

> 基础库 2.8.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.9.1](../../../framework/compatibility.html)
>
> **微信 iOS 版**：不支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [近场通信 (NFC)](../../../framework/device/nfc.html)

## [#](#功能描述) 功能描述

移除接收 NFC 设备消息事件的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onHCEMessage 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
const listener = function (res) { console.log(res) }

wx.onHCEMessage(listener)
wx.offHCEMessage(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.