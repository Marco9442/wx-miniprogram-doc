# [#](#iOS-端接入) iOS 端接入

微信小程序现已支持 iOS 端的虚拟支付服务，开发者可按照以下指引接入：

## [#](#一、基础功能) 一、基础功能

开发者需先开通小程序虚拟支付，并完成基础配置。可参考：[虚拟支付-产品介绍](../virtual-payment)

## [#](#二、功能开通) 二、功能开通

小程序同时满足以下条件：

- 已开通小程序虚拟支付
- 已配置小程序简称，配置指引：[微信开放社区](https://developers.weixin.qq.com/community/develop/doc/0004221455ce78d413893d4b75b009)

操作页面：[微信公众平台](https://mp.weixin.qq.com)-虚拟支付-基础配置

![](https://res8.wxqcloud.qq.com.cn/wxdoc/620a320e-e255-4e65-b9a0-b70126f3b860.png)
> 注意：为满足 Apple 支付对用户展示 display name 的要求，小程序需配置小程序简称

## [#](#三、道具、代币配置) 三、道具、代币配置

开发者配置的道具、代币均为 Android、iOS 双端互通，已配置的道具、代币可直接使用。

如需新增道具、代币也可直接使用原有方式，详见上文[基础功能](#一、基础功能)。

## [#](#四、用户下单) 四、用户下单

如需使用 Apple 支付，用户需同时满足如下条件：

- 用户使用 iPhone、iPad，且升级至 iOS 15 及以上；
- 用户微信客户端升级至 8.0.68 及以上；
- 最低支付金额为 1 元；
- 仅支持中国大陆的App Store账户；

可直接调用 [wx.requestVirtualPayment](https://developers.weixin.qq.com/miniprogram/dev/api/payment/wx.requestVirtualPayment.html)，平台会根据不同的设备类型、路由至对应的支付系统：

| 设备类型 | 对接支付系统 | 用户侧示意 |
| --- | --- | --- |
| Android、鸿蒙、Windows | 微信支付 |  |
| iOS | Apple 支付 |  |

> 注意：Apple 支付不支持使用沙箱环境，仅支持使用现网环境

## [#](#五、订单展示) 五、订单展示

平台提供页面、API 两种方式查看订单

- 页面：虚拟支付-交易订单，可通过支付渠道切换「普通支付」、「Apple 支付」
- API：可直接使用虚拟支付已提供的 `query_order` 接口查询订单

## [#](#六、用户退款) 六、用户退款

Apple 支付不支持开发者主动向用户发起退款，用户可在 App Store 申请退款，用户申请方式：

![](https://res8.wxqcloud.qq.com.cn/wxdoc/1e4e2fc6-5007-44a1-a3c8-be0455c98838.png)

用户申请后，Apple 支付会根据自身策略判断，并会向开发者发起重复三次的退款问询，开发者可根据自身策略响应问询。

Apple 支付只会参考开发者的问询结果，最终结果依然由 Apple 支付处理，详情可咨询苹果公司 (Apple) 。

消息推送和原有规范保持一致：[消息推送](https://developers.weixin.qq.com/miniprogram/dev/framework/server-ability/message-push)

##### [#](#响应接口：xpay-subscribe-ios-refund-query-notify) 响应接口：`xpay_subscribe_ios_refund_query_notify`

如果连续 3 次、在 3 秒内均未应答退款问询，微信平台会向 Apple 支付返回「不确定」作为退款参考，也即退款决定权交由苹果公司 (Apple) 处理。

##### [#](#消息内容：WxaVirtualPayIosRefundQueryNotifyEvent) 消息内容：`WxaVirtualPayIosRefundQueryNotifyEvent`

| 字段 | 类型 | 备注 |
| --- | --- | --- |
| refund\_time | string | 问询时间，Unix时间戳 |
| order\_time | string | 该笔退款的订单时间（退款订单对应的交易时间），Unix时间戳 |
| channel\_bill | string | Apple 支付票据号 |
| bundleid | string | 应用的 Apple bundleid |
| product\_id | string | 道具 id |
| p\_count | string | 道具/代币数量 |
| refund\_request\_reason | string | 用户请求退款的原因 |
| provide\_status | string | 发货状态，0 : 未发货 1：已发货 2：发货中 |
| pay\_order\_id | string | 退款对应支付订单号 |

##### [#](#应答响应：IosRefundQueryResponse) 应答响应：`IosRefundQueryResponse`

| 字段 | 类型 | 备注 |
| --- | --- | --- |
| result\_code | int32 | 结果码，0-放过，建议退款；1-拦截，拒绝退款 |
| result\_info | string | 结果描述 |
| evidence | string | 决策凭据(必填），业务需返回建议退款/拒绝退款的依据，用于退款审计 |

如 Apple 支付发起退款、并退款成功，平台会通过原有的退款推送 [xpay\_refund\_notify](../virtual-payment#退款推送xpay-refund-notify)

## [#](#七、结算入账) 七、结算入账

用户在 iOS 端支付的订单，由苹果公司 (Apple) 负责结算，详情可问询苹果公司 (Apple) 。

苹果公司 (Apple) 通常在自然月结束后 45～60 天内结算，并在扣除Apple佣金后，将款项结算给腾讯。

腾讯收到汇款后，会在第一时间将结算资金划转至开发者的虚拟支付账户，到账后即可提现。

## [#](#八、服务费率) 八、服务费率

在 iOS 端上进行的小程序虚拟支付，标准费率：17%。该部分费率包含苹果公司 (Apple) 、腾讯公司收取的两部分服务费。

为激励小程序开发者成长，推动小程序虚拟行业发展，腾讯的技术服务费在 2026 年限时减免。

| 科目 | 收取方 | 标准费率 | 2026 年 |
| --- | --- | --- | --- |
| Apple 服务费 | 苹果公司 (Apple) | 12% | 以苹果佣金政策为准，当前为12% |
| 腾讯技术服务费 | 腾讯公司 | 5% | 限时减免，0% |
| 合计 |  | 17% | 12% |

Incorrect translation.