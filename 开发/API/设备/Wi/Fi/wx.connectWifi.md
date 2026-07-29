# [#](#wx-connectWifi-Object-object) wx.connectWifi(Object object)

> 基础库 1.6.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.9.1](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [无线局域网 (Wi-Fi)](../../../framework/device/wifi.html)

## [#](#功能描述) 功能描述

连接 Wi-Fi。若已知 Wi-Fi 信息，可以直接利用该接口连接。仅 Android 与 iOS 11 以上版本支持。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| SSID | string |  | 是 | Wi-Fi 设备 SSID |  |
| BSSID | string |  | 否 | Wi-Fi 设备 BSSID |  |
| password | string |  | 是 | Wi-Fi 设备密码 |  |
| maunal | boolean | false | 否 | 跳转到系统设置页进行连接 | [2.12.0](../../../framework/compatibility.html) |
| partialInfo | boolean | false | 否 | 是否需要返回部分 Wi-Fi 信息，仅安卓生效 | [2.22.0](../../../framework/compatibility.html) |
| success | function |  | 否 | 接口调用成功的回调函数 |  |
| fail | function |  | 否 | 接口调用失败的回调函数 |  |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

## [#](#错误) 错误

| 错误码 | 错误信息 | 说明 |
| --- | --- | --- |
| 0 | ok | 正常 |
| 12000 | not init | 未先调用 `startWifi` 接口 |
| 12001 | system not support | 当前系统不支持相关能力 |
| 12002 | password error Wi-Fi | 密码错误 |
| 12003 | connection timeout | 连接超时, 仅 Android 支持 |
| 12004 | duplicate request | 重复连接 Wi-Fi |
| 12005 | wifi not turned on | Android 特有，未打开 Wi-Fi 开关 |
| 12006 | gps not turned on | Android 特有，未打开 GPS 定位开关 |
| 12007 | user denied | 用户拒绝授权链接 Wi-Fi |
| 12008 | invalid SSID | 无效 SSID |
| 12009 | system config err | 系统运营商配置拒绝连接 Wi-Fi |
| 12010 | system internal error | 系统其他错误，需要在 errmsg 打印具体的错误原因 |
| 12011 | weapp in background | 应用在后台无法配置 Wi-Fi |
| 12013 | wifi config may be expired | 系统保存的 Wi-Fi 配置过期，建议忘记 Wi-Fi 后重试，仅 Android 支持 |
| 12014 | invalid WEP / WPA password | iOS 特有，无效的 WEP / WPA 密码 |

## [#](#示例代码) 示例代码

```
wx.connectWifi({
  SSID: '',
  password: '',
  success (res) {
    console.log(res.errMsg)
  }
})
```

## [#](#注意) 注意

- Android 微信客户端 7.0.22 以上版本，connectWifi 的实现在 Android 10 及以上的手机无法生效，对于 Android 10 及以上版本，设备连接 wifi 之后，（受系统能力限制）其他进程无法使用当前连接的 wifi ；即连接上的 wifi 只对当前小程序有效，如果想要对整个系统生效，需要配置 maunal 来连接 wifi。
- iOS 系统底层没有给开发者提供因 wifi 密码错误而连接失败的事件，但用户可以收到密码错误的系统弹窗。建议开发者通过 onWifiConnected 事件来判断 wifi 是否连接成功；即设置定时器，若超时后仍没有 onWifiConnected 事件，则认定此次 wifi 连接无效。
- Android / iOS 在系统已经连上目标 wifi 的情况下，小程序再次连接目标 wifi，此时无论输入的密码是否正确，系统都会默认此次连接成功，且没有 onWifiConnected 事件。
- onWifiConnected 事件可能会返回空对象，此时代表 wifi 断开连接，开发者可忽略这种情况。

Incorrect translation.