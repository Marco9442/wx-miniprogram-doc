# [#](#NFCAdapter-wx-getNFCAdapter) [NFCAdapter](NFCAdapter.html) wx.getNFCAdapter()

> 基础库 2.11.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.11.2](../../../framework/compatibility.html)
>
> **微信 iOS 版**：不支持
>
> **微信 Android 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [近场通信 (NFC)](../../../framework/device/nfc.html)

## [#](#功能描述) 功能描述

获取 NFC 实例

## [#](#返回值) 返回值

### [#](#NFCAdapter) [NFCAdapter](NFCAdapter.html)

NFC 实例

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

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/1WsbDwmb75ig "在开发者工具中预览效果")

Incorrect translation.