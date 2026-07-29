# [#](#store-coupon) store-coupon

> 基础库 3.8.3 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 鸿蒙 OS 版**：支持

> 相关文档: [微信小店指引](https://developers.weixin.qq.com/doc/store/API/basics/component.html)

渲染框架支持情况：WebView

## [#](#功能描述) 功能描述

小程序内嵌微信小店优惠券，展示小店优惠券，并进行跳转交易。

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| appid | string |  | 是 | 小店appid。获取方式：[小店后台](https://store.weixin.qq.com/shop/setting/home) - 店铺管理 - 基础信息 - 账号信息 - 微信小店ID。 |  |
| coupon-id | string |  | 是 | 优惠券id。获取小店优惠券id，可以通过[小店后台](https://store.weixin.qq.com/shop/marketing/coupon) - 营销中心 - 优惠券。 |  |
| custom-style | object |  | 否 | 自定义样式。支持自定义的样式请查看custom-style。 |  |
| promoter-share-link | string |  | 否 | 推客参数。对于「机构推广券」类型优惠券，通过该参数，支持推客染色，可以通过[接口](https://developers.weixin.qq.com/doc/store/leagueheadsupplier/API/promotion/content/coupon/getcouponpromotersharelink.html)获取。 | [3.8.11](../framework/compatibility.html) |
| bindentersuccess | eventhandle |  | 否 | 跳转小店成功的回调。 |  |
| bindentererror | eventhandle |  | 否 | 跳转小店失败的回调，event.detail={code,message}。 |  |

## [#](#自定义样式-custom-style) 自定义样式(custom-style)

| 键名 | 说明 | 允许自定义的属性 |
| --- | --- | --- |
| card | 卡片样式 | background-color、width |
| discount-fee | 折扣金额样式（左上角） | color |
| coupon-type | 优惠券类型样式（左下角） | color |
| condition-text | 优惠使用条件样式（右上角） | color |
| valid-time | 优惠有效时间样式（右上角） | color |
| coupon-button | 优惠领取按钮样式 | border-radius、color、background-color |
| coupon-text-disabled | 优惠已领取状态样式 | color |
| coupon-footer-line | 卡片底部分割线样式 | background-color |
| coupon-shop-icon | 卡片底部logo icon样式 | fill、fill-opacity |
| coupon-shop-nickname | 卡片底部店铺昵称样式 | color |

## [#](#自定义样式-custom-style-示例代码) 自定义样式(custom-style)示例代码

```
<store-coupon appid="xxx" coupon-id="xxx" custom-style="{{customStyle}}" />
```

```
Page({
  data: {
    customStyle: {
      card: {
        'background-color': '#FAFAFA',
        'width': '300px',
      },
      'discount-fee': {
        color: 'rgba(0, 0, 0, 0.8)',
      },
      'coupon-type': {
        color: '#FF6146'
      },
      'condition-text': {
        color: '#FF6146'
      },
      'valid-time': {
        color: '#FF6146'
      },
      'coupon-button': {
        'border-radius': '30px',
        'background-color': 'rgba(0,0,0,0.9)',
        color: '#FFD48D',
      },
      'coupon-text-disabled': {
        color: '#FF6146'
      },
    },
  }
})
```

### [#](#detail-对象) detail 对象

| 属性名 | 类型 | 说明 |
| --- | --- | --- |
| code | Number | 状态码 |
| message | String | 错误信息 |

##### [#](#code-有效值) code 有效值

| 值 | 说明 |
| --- | --- |
| -1 | 系统失败，请重试 |
| 0 | 成功 |
| 109114、268542430 | 优惠券券不存在 |
| 109119 | 该类型优惠券不支持在小程序发放 |

## [#](#Bug-Tip) Bug & Tip

1. `tip`：平台规则限制，请保持组件内容完整展示，如需自定义样式请使用 custom-style 。组件元素数量和间距、商品保障内容及售卖数据、组件文字大小、“购买”按钮高度不可进行修改，若不符合要求则会导致组件不可用，并可能导致使用本组件的能力被封禁。
2. `tip`：暂不支持在微信 Windows 版和微信 Mac 版的小程序上使用本组件。
3. `tip`：参数 product-promotion-link、media-id 请在组件首次加载时传入，暂不支持在组件加载完成后调整参数
4. `tip`：暂不支持直播专享券、服务号限时活动券在小程序内发放

Incorrect translation.