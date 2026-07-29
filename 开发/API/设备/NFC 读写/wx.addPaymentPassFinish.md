# [#](#wx-addPaymentPassFinish-Object-args) wx.addPaymentPassFinish(Object args)

> 基础库 3.8.5 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持

## [#](#功能描述) 功能描述

通知客户端开卡成功

## [#](#参数) 参数

### [#](#Object-args) Object args

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| panid | String |  | 是 | addPaymentPassGetCertificateData传入的id |
| encryptedPassData | String |  | 是 | base64格式，详见PKAddPaymentPassRequest |
| ephemeralPublicKey | String |  | 是 | base64格式，详见PKAddPaymentPassRequest |
| activationData | String |  | 是 | base64格式，详见PKAddPaymentPassRequest |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#args-success-回调函数) args.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-object) Object object

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| result | String | 返回值 |
| errorMsg | String | 错误信息 |

## [#](#示例代码) 示例代码

```
const res = await wx.addPaymentPassFinish({
  panid: 'some_unique_chararaters',
  encryptedPassData: '', // base64
  ephemeralPublicKey: '', // base64
  activationData: '', // base64
});
```

Incorrect translation.