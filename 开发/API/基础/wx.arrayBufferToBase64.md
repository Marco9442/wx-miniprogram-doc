# [#](#string-wx-arrayBufferToBase64-ArrayBuffer-arrayBuffer) string wx.arrayBufferToBase64(ArrayBuffer arrayBuffer)

从基础库 [2.4.0](../../framework/compatibility.html) 开始，本接口停止维护

> 基础库 1.1.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

将 ArrayBuffer 对象转成 Base64 字符串

## [#](#参数) 参数

### [#](#ArrayBuffer-arrayBuffer) ArrayBuffer arrayBuffer

要转换成 Base64 字符串的 ArrayBuffer 对象

## [#](#返回值) 返回值

### [#](#string) string

Base64 字符串

## [#](#示例代码) 示例代码

```
const arrayBuffer = new Uint8Array([11, 22, 33])
const base64 = wx.arrayBufferToBase64(arrayBuffer)
```

Incorrect translation.