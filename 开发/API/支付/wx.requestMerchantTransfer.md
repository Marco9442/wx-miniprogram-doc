# [#](#wx-requestMerchantTransfer-Object-object) wx.requestMerchantTransfer(Object object)

> 基础库 3.3.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

商家转账用户确认模式下，在微信客户端通过小程序拉起页面请求用户确认收款。调用前需在微信支付商户平台/合作伙伴平台-产品中心，申请开通商家转账。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| mchId | string |  | 是 | 商户号 |
| subMchId | string |  | 否 | 子商户号，服务商模式下必填 |
| appId | string |  | 否 | 商户 appId，普通模式下必填，服务商模式下，appId 和 subAppId 二选一填写 |
| subAppId | string |  | 否 | 子商户 appId，服务商模式下，appId 和 subAppId 二选一填写 |
| package | string |  | 是 | 商家转账付款单跳转收款页 pkg 信息,商家转账付款单受理成功时返回给商户 |
| openId | string |  | 否 | 收款用户 openId， 对应传入的商户 appId 下，某用户的 openId |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
wx.requestMerchantTransfer({
  mchId: '',
  subMchId: '',
  appId: '',
  subAppId: '',
  package: '',
  openId: '',
  success (res) { },
  fail (res) { }
})
```

Incorrect translation.