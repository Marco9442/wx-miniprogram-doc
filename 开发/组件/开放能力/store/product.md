# [#](#store-product) store-product

> 基础库 3.5.5 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 鸿蒙 OS 版**：支持

> 相关文档: [微信小店指引](https://developers.weixin.qq.com/doc/store/API/basics/component.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

小程序内嵌微信小店商品，展示小店商品，并进行跳转交易。支持小店优选联盟带货跟佣功能。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | appid | string |  | 是 | 小店appid。获取方式：[小店后台](https://store.weixin.qq.com/shop/setting/home) - 店铺管理 - 基础信息 - 账号信息 - 微信小店ID。 | [3.5.5](../framework/compatibility.html) |
|  | product-id | string |  | 是 | 商品id。获取小店商品id，可以通过API获取([参考链接](https://developers.weixin.qq.com/doc/store/API/product/get.html))或通过[小店后台](https://store.weixin.qq.com/shop/goods/list) - 商品管理 - 商品列表 - 规格/编码获取。 | [3.5.5](../framework/compatibility.html) |
|  | product-promotion-link | string |  | 否 | 带货商品跟佣信息。若需要商品售卖时使用小店优选联盟带货跟佣功能，可以通过API获取带货商品跟佣信息([参考链接](https://developers.weixin.qq.com/doc/channels/API/windowproduct/get.html))。 | [3.5.5](../framework/compatibility.html) |
|  | media-id | string |  | 否 | 媒体文件id。可以通过API获取([参考链接](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/business-capabilities/cooperation_shop/upload.html#%E4%B8%80%E3%80%81%E4%B8%8A%E4%BC%A0%E8%B5%84%E6%96%99))。 | [3.7.1](../framework/compatibility.html) |
|  | custom-style | object |  | 否 | 自定义样式。支持自定义的样式请查看custom-style。 | [3.7.1](../framework/compatibility.html) |
|  | custom-content | boolean | false | 否 | 开启自定义插槽。开启后可自行控制卡片内容。 | [3.7.2](../framework/compatibility.html) |
|  | open-page | string | product-detail | 否 | 设置点击打开的页面(同时开启 custom-content 属性后生效)。 | [3.7.4](../framework/compatibility.html) |
|  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | product-detail | 商品详情页 | [3.7.4](../framework/compatibility.html) | | gift-product-detail | 送礼商品详情页 | [3.7.7](../framework/compatibility.html) | | buy | 下单页，只能支持「热招品牌且关联小店」商家 | [3.7.4](../framework/compatibility.html) | | gift | 送礼下单页，只能支持「热招品牌且关联小店」商家 | [3.15.1](../framework/compatibility.html) | | | | | | |
|  | logo-position | string | bottom-left | 否 | 设置小店标识的位置，不允许隐藏(同时开启 custom-content 属性后生效)。 | [3.7.2](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | bottom-left | 左下方 | | bottom-right | 右下方 | | | | | | |
|  | bindentersuccess | eventhandle |  | 否 | 跳转小店成功的回调。 | [3.7.1](../framework/compatibility.html) |
|  | bindentererror | eventhandle |  | 否 | 跳转小店失败的回调，event.detail={code,message}。 | [3.7.1](../framework/compatibility.html) |

## [#](#自定义样式-custom-style) 自定义样式(custom-style)

| 键名 | 说明 | 允许自定义的属性 |
| --- | --- | --- |
| card | 卡片样式 | background-color |
| title | 标题样式 | color |
| price | 价格样式 | color |
| buy-button | 购买按钮样式 | width、border-radius、color、background-color |
| buy-button-disabled | 购买按钮禁用态样式 | width、border-radius、color、background-color |

## [#](#自定义样式-custom-style-示例代码) 自定义样式(custom-style)示例代码

```
<store-product appid="xxx" product-id="xxx" custom-style="{{customStyle}}" />
```

```
Page({
  data: {
    customStyle: {
      card: {
        'background-color': '#FAFAFA',
      },
      title: {
        color: 'rgba(0, 0, 0, 0.8)',
      },
      price: {
        color: '#FF6146'
      },
      'buy-button': {
        width: '100px',
        'border-radius': '30px',
        'background-color': 'rgba(0,0,0,0.9)',
        color: '#FFD48D',
      },
      'buy-button-disabled': {
        width: '100px',
        'border-radius': '30px',
        'background-color': 'rgba(0,0,0,0.9)',
        color: '#FFD48D',
      },
    },
  }
})
```

## [#](#使用自定义插槽-custom-content-示例代码) 使用自定义插槽(custom-content)示例代码

```
<store-product appid="xxx" product-id="xxx" custom-content="{{true}}">
  <view>自定义卡片内容</view>
</store-product>
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
| 10001 | 无效的media-id |
| 10002 | 无效的media-id |
| 10003 | 文件正在上传中，请等待 |
| 10004 | 上传的文件存在风险，请重新上传 |
| 20001 | 该商品因违规已下架 |
| 60001 | 正在加载中 |
| 60002 | 正在渲染中 |
| 60004 | 加载异常 |
| 60005 | 加载失败 |

## [#](#Bug-Tip) Bug & Tip

1. `tip`：请保持组件的小店标识内容完整展示。
2. `tip`：参数 product-promotion-link、media-id 请在组件首次加载时传入，暂不支持在组件加载完成后调整参数
3. `tip`：暂不支持在微信 Windows 版和微信 Mac 版的小程序上使用本组件。

Incorrect translation.