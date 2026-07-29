# [#](#Object-wx-getBatteryInfoSync) Object wx.getBatteryInfoSync()

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.15.0](../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

[wx.getBatteryInfo](wx.getBatteryInfo.html) 的同步版本

## [#](#返回值) 返回值

### [#](#Object-res) Object res

| 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- |
| level | number | 设备电量，范围 1 - 100 |  |
| isCharging | boolean | 是否正在充电中 |  |
| isLowPowerModeEnabled | boolean | 是否处于省电模式 | [3.5.0](../../../framework/compatibility.html) |

Incorrect translation.