# [#](#wx-requestAppleSubscribeSign-Object-object) wx.requestAppleSubscribeSign(Object object)

> 基础库 3.16.1 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

发起苹果订阅签约

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | signData | Object |  | 是 | 具体支付参数见signData, 该参数需以string形式传递, 例如signData: '{"offerId":"123","productId":"testproductId","goodsPrice":10,"attach":"testdata"}' |
|  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | offerId | string |  | 是 | mp-支付基础配置中的offerid | |  | productId | string |  | 是 | 订阅道具 ID（需已配置为双端可用） | |  | goodsPrice | number |  | 是 | 道具单价(分), 用来校验价格与后台道具价格是否一致, 避免用户在业务商城页看到的价格与实际价格不一致导致投诉 | |  | activitySellingPrice | number |  | 否 | 首开优惠价格（分）。不填=原价签约；填大于0=优惠价签约（首开此价格，续费恢复原价）；填0=免费试用签约（首开 0 元，续费恢复原价） | |  | attach | string |  | 是 | 透传数据, 签约成功通知/发货通知时透传给开发者 | | | | | |
|  | paySig | string |  | 是 | 支付签名, 详见[《签名详解》](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/business-capabilities/virtual-payment.html) |
|  | signature | string |  | 是 | 用户态签名, 详见[《签名详解》](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/business-capabilities/virtual-payment.html) |

## [#](#错误) 错误

| 错误码 | 错误信息 | 说明 |
| --- | --- | --- |
| 1001 |  | 参数错误 |
| -1 |  | 支付失败 |
| -2 |  | 支付取消 |
| -4 |  | 风控拦截 |
| -5 |  | 开通签约结果未知 |
| -15001 |  | 参数错误,具体原因见err\_msg |
| -15002 |  | outTradeNo重复使用,请换新单号重试 |
| -15003 |  | 系统错误 |
| -15004 |  | currencyType错误,目前只能填CNY |
| -15005 |  | 用户态签名signature错误 |
| -15006 |  | 支付签名paySig错误 |
| -15007 |  | session\_key过期 |
| -15008 |  | 二级商户进件未完成 |
| -15009 |  | 代币未发布 |
| -15010 |  | 道具productId未发布 |
| -15011 |  | 现网版本的env只能是0,不能填1(沙盒环境) |
| -15012 |  | 调用米大师失败导致关单,请换新单号重试 |
| -15013 |  | goodsPrice道具价格错误 |
| -15014 |  | 道具/代币发布未生效，禁止下单，大概10分钟后生效 |
| -15016 |  | signData格式有问题 |
| -15017 |  | 此商家涉嫌违规，收款功能已被限制，暂无法支付。商家可以登录微信商户平台/微信支付商家助手小程序查看原因和解决方案 |
| -15018 |  | 代币或者道具productId审核不通过 |
| -15019 |  | 调微信报商户受限,商家可以登录微信商户平台/微信支付商家助手小程序查看原因和解决方案 |
| -15020 |  | 操作过快，请稍候再试 |
| -15021 |  | 小程序被限频交易 |

Incorrect translation.