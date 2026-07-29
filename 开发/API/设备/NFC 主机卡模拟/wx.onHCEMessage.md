# [#](#wx-onHCEMessage-function-listener) wx.onHCEMessage(function listener)

> 基础库 1.7.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.9.1](../../../framework/compatibility.html)
>
> **微信 iOS 版**：不支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [近场通信 (NFC)](../../../framework/device/nfc.html)

## [#](#功能描述) 功能描述

监听接收 NFC 设备消息事件。仅能注册一个监听

## [#](#参数) 参数

### [#](#function-listener) function listener

接收 NFC 设备消息事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 |
| --- | --- | --- | --- |
|  | messageType | number | 消息类型 |
|  | | 合法值 | 说明 | | --- | --- | | 1 | HCE APDU Command类型，小程序需对此指令进行处理，并调用 sendHCEMessage 接口返回处理指令 | | 2 | 设备离场事件类型 | | | |
|  | data | ArrayBuffer | `messageType=1` 时 ,客户端接收到 NFC 设备的指令 |
|  | reason | number | `messageType=2` 时，原因 |

Incorrect translation.