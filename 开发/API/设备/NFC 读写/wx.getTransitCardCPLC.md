# [#](#wx-getTransitCardCPLC-Object-object) wx.getTransitCardCPLC(Object object)

> 基础库 3.16.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 iOS 版**：不支持
>
> **微信 Android 版**：支持
>
> **微信 鸿蒙 OS 版**：不支持

## [#](#功能描述) 功能描述

仅 Android 可用。获取设备安全芯片的 CPLC（Card Production Life Cycle）标识信息，用于开卡前与发卡方 TSM 服务端交互

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-object-2) Object object

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| result | boolean | 返回值 |
| errorMsg | String | 错误信息 |
| cplc | String | 设备安全芯片的 CPLC 数据 |
| seid | String | 设备安全芯片的 SEID |
| walletVersionCode | String | 钱包版本号 |

## [#](#示例代码) 示例代码

```
const { result, errorMsg, cplc, seid, walletVersionCode } = await wx.getTransitCardCPLC();
```

Incorrect translation.