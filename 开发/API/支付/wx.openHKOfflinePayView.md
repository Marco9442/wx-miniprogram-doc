# [#](#wx-openHKOfflinePayView-Object-object) wx.openHKOfflinePayView(Object object)

> 基础库 3.4.4 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

拉起WeChat Pay HK付款码。

接入步骤：

1. 商户需已经开通微信港币钱包WeChat Pay HK的支付权限，
   2.请用商户在微信支付入驻时预留的邮箱，发起邮件申请接入权限：

- 【收件人】hkpayment@wechat.com
- 【邮件主题】申请接入拉起WeChat Pay HK付款码+商户名称：\*\*\*+商户号：\*\*\*
- 【邮件内容】因XXX原因（原因请按商户实际情况填写，不合理会驳回），需申请拉起WeChat Pay HK付款码，申请材料如下：
  - 商户名称
  - 商户号
  - 商户资质材料扫描件或照片（CI，BR任一），所有材料均需清晰，且有盖章
  - 拉起WeChat Pay HK付款码的场景说明：需有文字和示意图说明
  - 商户联系方式：邮件\*\*\*，联系电话\*\*\*

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | timeStamp | string |  | 是 | 时间戳，从 1970 年 1 月 1 日 00:00:00 至今的秒数，即当前的时间 |
|  | nonceStr | string |  | 是 | 随机字符串，长度为32个字符以下 |
|  | package | string |  | 是 | 业务数据包，开发者目前无需感知，直接传空字符串即可 |
|  | signType | string | SHA1 | 否 | 签名算法，应与后台下单时的值一致，目前仅支持 SHA1 |
|  | | 合法值 | 说明 | | --- | --- | | SHA1 | SHA1签名算法 | | | | | |
|  | paySign | string |  | 是 | 签名，具体见微信支付文档 |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
wx.openHKOfflinePayView({
  timeStamp: '',
  nonceStr: '',
  package: '',
  signType: 'SHA1',
  paySign: '',
  success (res) { },
  fail (res) { }
})
```

Incorrect translation.