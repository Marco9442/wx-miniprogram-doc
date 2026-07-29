# [#](#需适配的-API-汇总) 需适配的 API 汇总

- 多端框架是基于与小程序同源的技术实现，大部分的小程序 JSAPI 在多端应用中均可使用，但的确有部分的 API 因为产品载体已经变成为 App，无法再支持的，开发者需对这部分的 API 进行兼容性处理
- 为方便开发者对 API 进行兼容处理，本文将需开发者适配处理的 API 进行汇总

对于不支持的 API，通常可分为 3 种情况：

- 部分是有新的 API 进行替换或者是原有的 API 在参数上进行了一些调整：开发者使用条件编译语法进行兼容处理即可
- 部分 API 是尚未支持：是官方有计划支持或者已经在开发中，届时上线后，开发者使用条件编译语法进行兼容处理即可
- 部分 API 无法在 App 中支持：此种情况需开发者提前了解，需寻求其他替换方案或者在 App 中不提供相关功能

## [#](#一、需开发者进行适配兼容的接口) 一、需开发者进行适配兼容的接口

- 下方功能需使用新的 API 进行实现

| 名称 | 功能说明 | 需使用新 API |
| --- | --- | --- |
| wx.login | 小程序登录 | • 关于在 App 中实现登录的功能，平台提供了多种方案，涉及多个 API  • 详情可查看[微信登录说明](WeChatLogin) 以及[小程序登录适配方案说明](../../new-capability/auth/loginCompatible) |
| wx.showShareXXX | 转发（微信分享相关功能） | • 在 App 中使用微信分享（分享图片、分享文本、分享网页、分享小程序等）功能，需使用新的 wx.miniapp.shareXXXX 接口实现，详情可查看[转发](../total#%E8%BD%AC%E5%8F%91) |
| - | App 拉起小程序 | • 在 App 中拉起小程序需要使用新接口，详情可查看[wx.miniapp.launchMiniProgram](../miniapp/launchMiniProgram) |
| wx.requestPayment | 微信支付 | • 需使用新接口 [wx.miniapp.requestPayment](../miniapp/requestPayment)   • 部分 iOS 场景中，需使用苹果内购 IAP（In-App Purchase），详情可查看 [wx.miniapp.IAP](../miniapp/IAP) |
| wx.openCustomerServiceChat | 打开微信客服 | • 需使用新接口 [wx.miniapp.openCustomerServiceChat](../miniapp/openCustomerServiceChat) |
| wx.requestSubscribeMessage | 订阅消息 | • 小程序订阅消息能力在 App 中无法使用；  • App 中支持一次性订阅消息接口 [wx.miniapp.requestSubscribeMessage](../miniapp/requestSubscribeMessage)   - App 的消息推送可查看[消息推送使用指南](../../handbook/devtools/impush) |
| wx.getSystemInfo | 获取系统信息 | • 该接口的返回参数有所调整，详情可查看[wx.getSystemInfo](getSystemInfo)   • wx.getSystemInfoSync 的参数返回处理同 wx.getSystemInfo |
| wx.getAppBaseInfo | 获取 App 基础信息 | • 该接口的返回参数有所调整，详情可查看[wx.getAppBaseInfo](getAppBaseInfo) |
| wx.getLaunchOptionsSync | 获取本次应用启动时的参数 | • 该接口的返回参数有所调整，详情可查看[wx.getLaunchOptionsSync](getLaunchOptionsSync) |
| wx.getEnterOptionsSync | 获取应用启动时的参数 | • 该接口的返回参数有所调整，详情可查看[wx.getEnterOptionsSync](getEnterOptionsSync) |
| wx.getMenuButtonBoundingClientRect | 获取菜单按钮（右上角胶囊按钮）的布局位置信息 | • App 里不再呈现胶囊标识，该接口依旧返回相关坐标信息，便于开发者进行多端兼容 |
| wx.getBackgroundAudioManager | 获取全局唯一的背景音频管理器 | • 该接口是在小程序提供的同名 API 上拓展的，详情可查看[wx.getBackgroundAudioManager](getBackgroundAudioManager) |

## [#](#二、尚未支持的接口) 二、尚未支持的接口

- 包含暂无计划支持和已在开发中的接口，详情可查看 [API 总览](../total)

Incorrect translation.