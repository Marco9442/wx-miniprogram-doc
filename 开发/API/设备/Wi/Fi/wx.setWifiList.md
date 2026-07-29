# [#](#wx-setWifiList-Object-object) wx.setWifiList(Object object)

> 基础库 1.6.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.9.1](../../../framework/compatibility.html)

> 相关文档: [无线局域网 (Wi-Fi)](../../../framework/device/wifi.html)

## [#](#功能描述) 功能描述

设置 `wifiList` 中 AP 的相关信息。在 `onGetWifiList` 回调后调用，**iOS特有接口**。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | wifiList | Array.<Object> |  | 是 | 提供预设的 Wi-Fi 信息列表 |
|  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | SSID | string |  | 否 | Wi-Fi 的 SSID | |  | BSSID | string |  | 否 | Wi-Fi 的 BSSID | |  | password | string |  | 否 | Wi-Fi 设备密码 | | | | | |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

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

## [#](#注意) 注意

- 该接口只能在 `onGetWifiList` 回调之后才能调用。
- 此时客户端会挂起，等待小程序设置 Wi-Fi 信息，请务必尽快调用该接口，若无数据请传入一个空数组。
- 有可能随着周边 Wi-Fi 列表的刷新，单个流程内收到多次带有存在重复的 Wi-Fi 列表的回调。

## [#](#示例代码) 示例代码

```
wx.onGetWifiList(function(res) {
  if (res.wifiList.length) {
    wx.setWifiList({
      wifiList: [{
        SSID: res.wifiList[0].SSID,
        BSSID: res.wifiList[0].BSSID,
        password: '123456'
      }]
    })
  } else {
    wx.setWifiList({
      wifiList: []
    })
  }
})
wx.getWifiList()
```

Incorrect translation.