# [#](#NFCAdapter-onDiscovered-function-listener) NFCAdapter.onDiscovered(function listener)

> 基础库 2.11.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持
>
> **微信 iOS 版**：不支持
>
> **微信 Android 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [近场通信 (NFC)](../../../framework/device/nfc.html)

## [#](#功能描述) 功能描述

监听 NFC Tag

## [#](#参数) 参数

### [#](#function-listener) function listener

的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| id | ArrayBuffer |  |
| techs | Array | tech 数组，用于匹配NFC卡片具体可以使用什么标准（NfcA等实例）处理 |
| messages | Array | 可选，NdefMessage 数组，消息格式为 {id: ArrayBuffer, type: ArrayBuffer, payload: ArrayBuffer} |

Incorrect translation.