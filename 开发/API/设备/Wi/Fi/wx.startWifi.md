# [#](#wx-startWifi-Object-object) wx.startWifi(Object object)

> 基础库 1.6.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.9.1](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [无线局域网 (Wi-Fi)](../../../framework/device/wifi.html)

## [#](#功能描述) 功能描述

初始化 Wi-Fi 模块。

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

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/8P7zrkmd7r2n "在开发者工具中预览效果")

```
wx.startWifi({
  success (res) {
    console.log(res.errMsg)
  }
})
```

Incorrect translation.