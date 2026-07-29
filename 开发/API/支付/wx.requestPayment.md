# [#](#wx-requestPayment-Object-object) wx.requestPayment(Object object)

> **以 [Promise 风格](../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

发起微信支付。调用前需在[小程序微信公众平台](https://mp.weixin.qq.com/)-功能-微信支付入口申请接入微信支付。了解更多信息，可以参考 [微信支付开发文档](https://pay.weixin.qq.com/doc/v3/partner/4012069852)：

【普通商户】

- [产品介绍](https://pay.weixin.qq.com/doc/v3/merchant/4012791894)
- [开发指引](https://pay.weixin.qq.com/doc/v3/merchant/4012791911)
- [下单接口](https://pay.weixin.qq.com/doc/v3/merchant/4012791897)
- [调起支付接口](https://pay.weixin.qq.com/doc/v3/merchant/4012791898)

【普通服务商】

- [产品介绍](https://pay.weixin.qq.com/doc/v3/partner/4012085810)
- [开发指引](https://pay.weixin.qq.com/doc/v3/partner/4012076732)
- [下单接口](https://pay.weixin.qq.com/doc/v3/partner/4012759974)
- [调起支付接口](https://pay.weixin.qq.com/doc/v3/partner/4012085827)

【旧版本 (v2)】

- [开发指引](https://pay.weixin.qq.com/doc/v2/merchant/4011938514)
- [支付接口](https://pay.weixin.qq.com/doc/v2/merchant/4011939566)

如果使用[云开发](https://developers.weixin.qq.com/miniprogram/dev/wxcloud/basis/getting-started.html)，则 `wx.requestPayment` 所需参数可以通过云开发微信支付统一下单接口免鉴权获取、并可免证书、免签名的安全调用微信支付服务端接口、及接收异步支付结果回调，详见[云开发微信支付](/miniprogram/dev/wxcloud/guide/wechatpay/wechatpay.html)。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | timeStamp | string |  | 是 | 时间戳，从 1970 年 1 月 1 日 00:00:00 至今的秒数，即当前的时间 |
|  | nonceStr | string |  | 是 | 随机字符串，长度为32个字符以下 |
|  | package | string |  | 是 | 统一下单接口返回的 prepay\_id 参数值，提交格式如：prepay\_id=\*\*\* |
|  | signType | string | MD5 | 否 | 签名算法，应与后台下单时的值一致 |
|  | | 合法值 | 说明 | | --- | --- | | MD5 | 仅在 v2 版本接口适用 | | HMAC-SHA256 | 仅在 v2 版本接口适用 | | RSA | 仅在 v3 版本接口适用 | | | | | |
|  | paySign | string |  | 是 | 签名，具体见微信支付文档 |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
wx.requestPayment({
  timeStamp: '',
  nonceStr: '',
  package: '',
  signType: 'MD5',
  paySign: '',
  success (res) { },
  fail (res) { }
})
```

注：如果服务端有使用云开发，可以通过云开发微信支付[统一下单](https://developers.weixin.qq.com/miniprogram/dev/wxcloud/reference-sdk-api/open/pay/CloudPay.unifiedOrder.html)接口免鉴权获取以上所需所有参数，示例：

```
// 云函数代码
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})

exports.main = async (event, context) => {
  const res = await cloud.cloudPay.unifiedOrder({
    "body" : "小秋TIT店-超市",
    "outTradeNo" : "1217752501201407033233368018",
    "spbillCreateIp" : "127.0.0.1",
    "subMchId" : "1900009231",
    "totalFee" : 1,
    "envId": "test-f0b102",
    "functionName": "pay_cb"
  })
  return res
}

// 小程序代码
wx.cloud.callFunction({
  name: '函数名',
  data: {
    // ...
  },
  success: res => {
    const payment = res.result.payment
    wx.requestPayment({
      ...payment,
      success (res) {
        console.log('pay success', res)
      },
      fail (err) {
        console.error('pay fail', err)
      }
    })
  },
  fail: console.error,
})
```

Incorrect translation.