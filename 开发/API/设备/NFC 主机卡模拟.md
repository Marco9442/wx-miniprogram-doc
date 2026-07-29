# [#](#wx-stopHCE-Object-object) wx.stopHCE(Object object)

> 基础库 1.7.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.1.0](../../../framework/compatibility.html)
>
> **微信 iOS 版**：不支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [近场通信 (NFC)](../../../framework/device/nfc.html)

## [#](#功能描述) 功能描述

关闭 NFC 模块。仅在安卓与鸿蒙系统下有效。

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
| 0 | ok | 正常 |
| 13000 |  | 当前设备不支持NFC |
| 13001 |  | 当前设备支持NFC，但系统NFC开关未开启 |
| 13002 |  | 当前设备支持NFC，但不支持HCE |
| 13003 |  | AID列表参数格式错误 |
| 13004 |  | 未设置微信为默认NFC支付应用 |
| 13005 |  | 返回的指令不合法 |
| 13006 |  | 注册AID失败 |

## [#](#示例代码) 示例代码

```
wx.stopHCE({
  success (res) {
    console.log(res.errMsg)
  }
})
```

Incorrect translation.