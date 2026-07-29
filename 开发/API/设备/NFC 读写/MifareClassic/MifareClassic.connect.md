# [#](#MifareClassic-connect-Object-object) MifareClassic.connect(Object object)

> 基础库 2.11.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：支持
>
> **微信 iOS 版**：不支持
>
> **微信 Android 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [近场通信 (NFC)](../../../framework/device/nfc.html)

## [#](#功能描述) 功能描述

连接 NFC 标签

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#错误) 错误

| 错误码 | 错误信息 | 说明 |
| --- | --- | --- |
| 13000 | 设备不支持NFC |  |
| 13001 | 系统NFC开关未打开 |  |
| 13010 | 未知错误 |  |
| 13019 | user is not authorized | 用户未授权 |
| 13011 | invalid parameter | 参数无效 |
| 13012 | parse NdefMessage failed | 将参数解析为NdefMessage失败 |
| 13021 | NFC discovery already started | 已经开始NFC扫描 |
| 13018 | NFC discovery has not started | 尝试在未开始NFC扫描时停止NFC扫描 |
| 13022 | Tech already connected | 标签已经连接 |
| 13023 | Tech has not connected | 尝试在未连接标签时断开连接 |
| 13013 | NFC tag has not been discovered | 未扫描到NFC标签 |
| 13014 | invalid tech | 无效的标签技术 |
| 13015 | unavailable tech | 从标签上获取对应技术失败 |
| 13024 | function not support | 当前标签技术不支持该功能 |
| 13017 | system internal error | 相关读写操作失败 |
| 13016 | connect fail | 连接失败 |

Incorrect translation.