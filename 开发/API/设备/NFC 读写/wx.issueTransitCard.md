# [#](#wx-issueTransitCard-Object-args) wx.issueTransitCard(Object args)

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

仅 Android 可用。拉起厂商钱包开卡流程，在设备安全芯片（eSE）中写入交通卡

## [#](#参数) 参数

### [#](#Object-args) Object args

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| issuerID | String |  | 是 | 交通卡卡种标识 |
| orderNo | String |  | 是 | 开卡订单号 |
| operation | String |  | 是 | 操作类型："1"=普通开卡，"2"=卡片迁入 |
| sign | String |  | 是 | 请求签名 |
| timestamp | String |  | 否 | 签名时间戳（毫秒） |
| entrustId | String |  | 否 | 签约订单号，仅先乘后付业务需要 |
| paymentMode | String |  | 否 | 支付方式："1"=微信支付，"2"=支付宝支付，"3"=银联支付 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#args-success-回调函数) args.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-object) Object object

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | String | 错误信息 |
| errno | Number | 错误码，0 表示成功 |
| cardNo | String | 开卡成功后的交通卡卡号 |
| errorCode | Number | 失败时返回微信统一错误码 |

## [#](#示例代码) 示例代码

```
const { errMsg, errno, cardNo, errorCode } = await wx.issueTransitCard({
  issuerID: 'changsha',
  orderNo: 'order_xxx',
  operation: '1',
  sign: 'sign_xxx',
  timestamp: '1710000000000',
});
```

Incorrect translation.