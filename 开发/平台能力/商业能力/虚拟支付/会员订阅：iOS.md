# [#](#会员订阅：iOS) 会员订阅：iOS

## [#](#一、概述) 一、概述

### [#](#_1-能力说明) 1. 能力说明

小程序虚拟支付在 iOS 端提供会员订阅能力。用户完成一次签约后，由 Apple 按周期自动扣费。

| 特性 | 说明 |
| --- | --- |
| 签约入口 | `wx.requestAppleSubscribeSign` |
| 扣款方 | **Apple 自动续费**（非开发者发起） |
| 退订方式 | 用户在 App Store 设置中退订 |
| 费率 | **12%**（Apple 佣金） |
| 物品互通 | 订阅物品安卓、苹果**双端通用** |
| 版本要求 | 微信客户端 **≥ 8.0.71**，小程序基础库 **≥ 3.16.1** |

### [#](#_2-支持的签约类型) 2. 支持的签约类型

| 签约类型 | 说明 | 首开价格 | 续费价格 |
| --- | --- | --- | --- |
| 原价 | 首开和续费均为原价 | 物品原价 | 物品原价 |
| 优惠价 | 首开优惠，续费恢复原价 | 自定义优惠价 | 物品原价 |
| 免费试用 | 首开 0 元，续费恢复原价 | 0 元 | 物品原价 |

![](https://res8.wxqcloud.qq.com.cn/wxdoc/ebdd7986-af78-40e4-a3dc-07b2d84c5257.png)

### [#](#_3-准入条件) 3. 准入条件

| # | 条件 | 说明 |
| --- | --- | --- |
| 1 | 已接入小程序虚拟支付 | 基础前提 |
| 2 | **已开通 iOS 支付** | 苹果订阅依赖 iOS 支付通道，必须先完成 iOS 支付接入 |
| 3 | **已开通小程序订阅制** | 安卓和苹果的订阅均需提前开通小程序订阅制 |

---

## [#](#二、接入流程) 二、接入流程

### [#](#Step-1：申请开通) Step 1：申请开通

**收件人**：wx\_virtualpayment@tencent.com

**前置条件**：

1. 已接入小程序虚拟支付
2. 小程序首次发布时间至今 **≥ 90 天**
3. 小程序完成**认证备案**
4. 近 30 天日均 DAU **≥ 1 万**

**邮件主题**：`申请开通小程序订阅 - 小程序昵称 - 申请日期`

**邮件正文**：

```
小程序昵称：
小程序appid：
虚拟支付商户号：
小程序主体：
小程序类目：
业务模式：主营业务、小程序 DAU、交易金额
申请用途：苹果订阅相关产品
页面交互：（开通、续费、管理流程，图片 jpg/png 格式，文件大小不超过 2MB）
```

交互示意：

![](https://res8.wxqcloud.qq.com.cn/wxdoc/b296fb7e-0dbb-4603-a86a-8ff3e74f5d39.png)

**交互图片注意事项**：

1. 不允许使用拍照图片
2. 需将完整交互放在一张图片中
3. 购买记录页面需要出现客服电话，且客服电话需要完成[认证](https://kf.qq.com/faq/1709123am2qa1709122mMR7N.html)

---

### [#](#Step-2：物品配置) Step 2：物品配置

在 MP 后台配置订阅道具，配置方式与安卓订阅一致：

> 小程序后台 → 虚拟支付 → 基础配置 → 道具配置 → 添加道具 → 选择「会员订阅」

> 物品的 `product_id` 在安卓和苹果端通用，不需要为苹果端单独创建新的订阅物品。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/8ac20e69-b643-4819-b277-8cf7013c3c7b.png) 

---

### [#](#Step-3：苹果订阅签约) Step 3：苹果订阅签约

> **签约前提**：若用户已签约并完成解约，需等待当前订阅周期结束后，才能再次发起签约。

#### [#](#_3-1-接口说明) 3.1 接口说明

| 项目 | 说明 |
| --- | --- |
| 接口名 | `wx.requestAppleSubscribeSign` |
| 用途 | 调起苹果订阅签约支付页（iOS 端使用） |
| 版本要求 | 微信客户端 ≥ 8.0.71，小程序基础库 ≥ 3.16.1 |

#### [#](#_3-2-入参) 3.2 入参

| 层级 | 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| **顶层** | signData | string | 是 | 支付参数，需通过 `JSON.stringify()` 转为字符串 |
|  | paySig | string | 是 | 支付签名，计算方式：`to_hex(hmac_sha256(appKey, uri + '&' + signData))`，appKey 见 MP 后台虚拟支付基础配置 |
|  | signature | string | 是 | 用户态签名，计算方式同 `paySig` |
|  | success | function | 否 | 接口调用成功的回调函数 |
|  | fail | function | 否 | 接口调用失败的回调函数 |
|  | complete | function | 否 | 接口调用结束的回调函数（成功、失败都会执行） |
| **signData** | offerId | string | 是 | 支付侧申请的应用 ID |
|  | productId | string | 是 | 订阅道具 ID |
|  | goodsPrice | number | 是 | 道具单价（单位：分） |
|  | activitySellingPrice | number | 否 | 见下方签约类型控制 |
|  | attach | string | 是 | 透传数据，签约成功通知 / 发货通知时透传给开发者，字段长度不要超过 200，不允许有特殊字符 |

#### [#](#_3-3-签约类型控制) 3.3 签约类型控制

三种签约类型通过 `activitySellingPrice` 参数控制：

| 签约类型 | activitySellingPrice | 效果 |
| --- | --- | --- |
| 原价签约 | 不填 | 首开和续费均为原价 |
| 优惠价签约 | 填大于 0 的值 | 首开为优惠价，续费恢复原价 |
| 免费试用 | 填 `0` | 首开 0 元，续费恢复原价 |

#### [#](#_3-4-调用示例) 3.4 调用示例

**原价签约**：

```
wx.requestAppleSubscribeSign({
  signData: JSON.stringify({
    offerId: '1450032323',
    productId: 'subscription_vip_monthly',
    goodsPrice: 3000,
    attach: 'uid=12345'
  }),
  paySig: '...',
  signature: '...',
  success(res) { /* 拉起成功 */ },
  fail(err) { /* 用户取消或失败 */ }
})
```

**优惠价签约**（首开 9.9 元，续费恢复原价 30 元）：

```
wx.requestAppleSubscribeSign({
  signData: JSON.stringify({
    offerId: '1450032323',
    productId: 'subscription_vip_monthly',
    goodsPrice: 3000,
    activitySellingPrice: 990,
    attach: 'uid=12345'
  }),
  paySig: '...',
  signature: '...',
  success(res) { /* 拉起成功 */ },
  fail(err) { /* 用户取消或失败 */ }
})
```

**免费试用签约**（首开 0 元，续费恢复原价）：

```
wx.requestAppleSubscribeSign({
  signData: JSON.stringify({
    offerId: '1450032323',
    productId: 'subscription_vip_monthly',
    goodsPrice: 3000,
    activitySellingPrice: 0,
    attach: 'uid=12345'
  }),
  paySig: '...',
  signature: '...',
  success(res) { /* 拉起成功 */ },
  fail(err) { /* 用户取消或失败 */ }
})
```

> **注意**：该接口返回值**不能作为签约成功的判定标准**，需以签约成功通知或签约查询结果为准。

---

### [#](#Step-4：接收通知) Step 4：接收通知

#### [#](#_4-1-通知场景) 4.1 通知场景

| 场景 | 通知事件 | 说明 |
| --- | --- | --- |
| 签约成功 | `xpay_apple_subscribe_signing_result_notify` | 用户首次签约成功，告知开发者建立签约关系、开通权益 |
| 扣款成功 | `xpay_goods_deliver_notify` | 扣款成功，开发者发货或延长会员有效期 |
| 解约（退订） | `xpay_apple_subscribe_unsigning_result_notify` | 用户关闭自动续费（解约）时下发 |

#### [#](#_4-2-签约成功通知（xpay-apple-subscribe-signing-result-notify）) 4.2 签约成功通知（`xpay_apple_subscribe_signing_result_notify`）

**触发时机**：用户首次签约成功时下发一次。续费场景不会再次发送此通知。

**基础字段**：

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| ToUserName | String | 小程序原始 ID |
| FromUserName | String | openid |
| CreateTime | Number | 消息发送时间 |
| MsgType | String | 消息类型，固定为 `event` |
| Event | String | 事件类型 `xpay_apple_subscribe_signing_result_notify` |
| OpenId | String | 用户 openid |
| Attach | String | 签约时透传的 `attach` |
| AppleSubscriptionInfo | Object | 苹果订阅签约信息，详见下方 |

**AppleSubscriptionInfo 内容**：

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| OriginalTransactionId | String | 首次订阅的苹果原始交易 ID，用于标识同一条订阅关系 |
| ProductId | String | 订阅道具 ID |
| AutoRenewStatus | Number | 自动续费状态：`1` 开启 / `0` 关闭 |
| RenewalDate | Number | 下次续费时间（毫秒级 Unix 时间戳） |
| SignedTime | Number | 签约成功时间（毫秒级 Unix 时间戳） |

#### [#](#_4-3-扣款发货通知（xpay-goods-deliver-notify）) 4.3 扣款发货通知（`xpay_goods_deliver_notify`）

**触发时机**：每次扣款成功后下发。首次扣款与后续自动续费扣款通知格式一致。

**基础字段**：

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| ToUserName | String | 小程序原始 ID |
| FromUserName | String | 该事件消息的 openid，固定为微信官方的 openid |
| CreateTime | Number | 消息发送时间 |
| MsgType | String | 消息类型，固定为 `event` |
| Event | String | 事件类型 `xpay_goods_deliver_notify` |
| OpenId | String | 用户 openid |
| OutTradeNo | String | 业务订单号 |
| WeChatPayInfo | Object | 支付信息 |
| GoodsInfo | Object | 道具参数信息 |
| AppleSubscriptionInfo | Object | 苹果订阅关系信息（苹果订阅场景携带；安卓订阅 / 普通支付不携带） |

**GoodsInfo 内容**：

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| ProductId | String | 道具 ID |
| Quantity | Number | 数量 |
| OrigPrice | Number | 物品原始价格（单位：分） |
| ActualPrice | Number | 物品实际支付价格（单位：分） |
| Attach | String | 透传信息 |

**AppleSubscriptionInfo 内容**：

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| OriginalTransactionId | String | 首次订阅的苹果原始交易 ID，用于标识同一条订阅关系 |
| AutoRenewStatus | Number | 自动续费状态：`1` 开启 / `0` 关闭 |
| RenewalDate | Number | 下次续费时间（毫秒级 Unix 时间戳） |

#### [#](#_4-4-解约通知（xpay-apple-subscribe-unsigning-result-notify）) 4.4 解约通知（`xpay_apple_subscribe_unsigning_result_notify`）

**触发时机**：用户关闭自动续费（解约）时下发。

**基础字段**：

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| ToUserName | String | 小程序原始 ID |
| FromUserName | String | openid |
| CreateTime | Number | 消息发送时间 |
| MsgType | String | 消息类型，固定为 `event` |
| Event | String | 事件类型 `xpay_apple_subscribe_unsigning_result_notify` |
| OpenId | String | 用户 openid |
| Attach | String | 签约时透传的 `attach` |
| Action | String | 动作类型，固定为 `unsubscribe` |
| AppleSubscriptionInfo | Object | 苹果订阅解约信息，详见下方 |

**AppleSubscriptionInfo 内容**：

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| OriginalTransactionId | String | 首次订阅的苹果原始交易 ID，用于标识同一条订阅关系 |
| ProductId | String | 订阅道具 ID（开发者的 out\_product\_id） |
| AutoRenewStatus | Number | 自动续费状态，解约时固定为 `0`（已关闭） |
| RenewalDate | Number | 订阅到期时间（毫秒级 Unix 时间戳），即当前订阅周期的结束时间 |
| UnsignedTime | Number | 解约时间（毫秒级 Unix 时间戳） |

#### [#](#_4-5-返回参数) 4.5 返回参数

各类通知的返回格式一致，开发者收到通知后需按以下格式返回：

| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ErrCode | Number | 是 | 处理状态：`0` 成功，其他为失败 |
| ErrMsg | String | 否 | 错误原因，用于调试 |

XML 示例：

```
<xml>
  <ErrCode>0</ErrCode>
  <ErrMsg>success</ErrMsg>
</xml>
```

---

### [#](#Step-5：平台自动写入苹果订阅订单) Step 5：平台自动写入苹果订阅订单

#### [#](#_5-1-背景) 5.1 背景

苹果订阅的扣款由 Apple 自动发起，小程序平台无法主动发起扣款，只能被动接收 Apple 的扣款通知。为保证订单数据完整，平台会在收到 Apple 扣款通知后，自动在虚拟支付订单表中写入一条苹果订阅扣款成功的订单记录，订单类型标记为苹果订阅。

#### [#](#_5-2-写入时机) 5.2 写入时机

平台收到 Apple 的扣款通知后：

- 向开发者推送 `xpay_goods_deliver_notify`（开发者处理发货）
- 同步在平台订单库写入一条订单记录（订单类型 = 苹果订阅）

---

### [#](#Step-6：订阅状态查询) Step 6：订阅状态查询

开发者可随时查询用户的订阅状态，包括自动续费开关、下次续费时间等。

#### [#](#_6-1-接口说明) 6.1 接口说明

| 项目 | 说明 |
| --- | --- |
| 接口地址 | `POST https://api.weixin.qq.com/xpay/query_subscribe_contract?access_token=ACCESS_TOKEN&pay_sig=PAY_SIG` |
| 查询口径 | 通过 `mode` 字段区分安卓 / 苹果订阅；不填默认查安卓订阅 |
| 注意事项 | 苹果订阅状态更新依赖苹果通知，苹果通知最多有 **10 秒** 延迟 |

#### [#](#_6-2-请求参数) 6.2 请求参数

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | String | 否 | 查询模式：`android`（默认）/ `apple` |
| openid | String | 是 | 用户 openid |
| product\_id | String | 是 | 道具 ID，需为订阅制道具 |
| out\_contract\_code | String | 否 | `mode=android` 时必传，签约时传入的协议号 |

#### [#](#_6-3-响应参数) 6.3 响应参数

**公共响应**：

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| errcode | Number | 错误码，`0` 表示成功 |
| errmsg | String | 错误信息 |
| authorization\_state | String | 签约授权状态：`SIGNED` 签约生效中 / `TERMINATED` 已解约 / `UNBINDUSER` 从未签约 |
| apple\_subscription\_info | Object | 苹果订阅信息（仅 `mode=apple` 返回） |

**apple\_subscription\_info 内容**：

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| original\_transaction\_id | String | 首次订阅的苹果原始交易 ID |
| auto\_renew\_status | Number | 自动续费状态：`1` 开启 / `0` 关闭 |
| recent\_subscription\_start\_date | Number | 在一系列订阅购买中，自动续订订阅的最早起始日期；该日期将忽略所有时长为 60 天或更短的付费服务中断期（毫秒级 Unix 时间戳） |
| renewal\_date | Number | 下次续费到期时间（毫秒级 Unix 时间戳） |

#### [#](#_6-4-响应示例（mode-apple）) 6.4 响应示例（mode=apple）

```
{
  "errcode": 0,
  "errmsg": "ok",
  "authorization_state": "SIGNED",
  "apple_subscription_info": {
    "original_transaction_id": "2000001147426510",
    "auto_renew_status": 1,
    "recent_subscription_start_date": 1775226065000,
    "renewal_date": 1775226245000
  }
}
```

---

### [#](#Step-7：退款处理) Step 7：退款处理

#### [#](#_7-1-退款基本规则) 7.1 退款基本规则

- **Apple 支付不支持开发者主动向用户发起退款**
- 用户可在 **App Store** 申请退款

![](https://res8.wxqcloud.qq.com.cn/wxdoc/f98419c5-23a4-4985-8b8f-b05ad993a5e0.png)

#### [#](#_7-2-用户申请退款流程) 7.2 用户申请退款流程

1. 用户在 App Store 提出退款申请
2. Apple 支付根据自身策略判断，并向开发者发起**连续三次**退款问询
3. 开发者可根据自身策略响应问询
4. Apple 支付只会**参考**开发者的问询结果，**最终结果仍由 Apple 支付处理**

> 详情可咨询苹果公司（Apple）。

#### [#](#_7-3-退款问询通知（xpay-subscribe-ios-refund-query-notify）) 7.3 退款问询通知（`xpay_subscribe_ios_refund_query_notify`）

消息推送和原有规范保持一致：[消息推送](https://developers.weixin.qq.com/miniprogram/dev/framework/server-ability/message-push)

> **重要提示**：如果连续 3 次、在 3 秒内均未应答退款问询，微信平台会向 Apple 支付返回\*\*「不确定」\*\*作为退款参考，也即退款决定权交由苹果公司（Apple）处理。

**问询消息内容**（`WxaVirtualPayIosRefundQueryNotifyEvent`）：

| 字段 | 类型 | 备注 |
| --- | --- | --- |
| `refund_time` | string | 问询时间，Unix 时间戳 |
| `order_time` | string | 该笔退款的订单时间（退款订单对应的交易时间），Unix 时间戳 |
| `channel_bill` | string | Apple 支付票据号 |
| `bundleid` | string | 应用的 Apple bundleid |
| `product_id` | string | 道具 id |
| `p_count` | string | 道具 / 代币数量 |
| `refund_request_reason` | string | 用户请求退款的原因 |
| `provide_status` | string | 发货状态，0：未发货，1：已发货，2：发货中 |
| `pay_order_id` | string | 退款对应支付订单号 |

#### [#](#_7-4-应答响应（IosRefundQueryResponse）) 7.4 应答响应（`IosRefundQueryResponse`）

| 字段 | 类型 | 备注 |
| --- | --- | --- |
| `result_code` | int32 | 结果码，**0** - 放过（建议退款）；**1** - 拦截（拒绝退款） |
| `result_info` | string | 结果描述 |
| `evidence` | string | 决策凭据（**必填**），业务需返回建议退款 / 拒绝退款的依据，用于退款审计 |

#### [#](#_7-5-退款成功后续通知) 7.5 退款成功后续通知

如 Apple 支付发起退款并退款成功，平台会通过**原有的退款推送**接口通知开发者：

- 接口名：**`xpay_refund_notify`**
- 详细文档参考：[虚拟支付-退款推送](virtual-payment#退款推送xpay-refund-notify)

Incorrect translation.