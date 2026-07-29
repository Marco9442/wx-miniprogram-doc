# [#](#wx-checkTransitCardSupport-Object-args) wx.checkTransitCardSupport(Object args)

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

仅 Android 可用。检查当前设备是否支持对指定交通卡执行 NFC 操作（包括 NFC 硬件、安全芯片、钱包 APP 状态、卡片冲突等综合检查）

## [#](#参数) 参数

### [#](#Object-args) Object args

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| issuerID | String |  | 是 | 交通卡卡种标识 |
| actionType | String |  | 否 | 要检查的操作类型，可选值："issue"（开卡）、"recharge"（充值）、"delete"（删卡），默认 "issue" |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#args-success-回调函数) args.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-object) Object object

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| result | boolean | 返回值 |
| errorMsg | String | 错误信息 |
| supportNFC | boolean | 设备是否支持 NFC |
| supportSE | boolean | 设备是否支持安全芯片（eSE） |
| walletReady | boolean | 厂商钱包 APP 是否就绪（已安装且版本满足要求） |
| hasConflictCard | boolean | 是否存在冲突卡片（同一 issuerID 对应的卡已存在或存在互斥卡种） |

## [#](#示例代码) 示例代码

```
const { result, errorMsg, supportNFC, supportSE, walletReady, hasConflictCard } = await wx.checkTransitCardSupport({
  issuerID: 'changsha',
  actionType: 'issue',
});
```

Incorrect translation.