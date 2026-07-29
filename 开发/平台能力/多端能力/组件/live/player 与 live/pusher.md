# [#](#live-player-与-live-pusher-使用说明) live-player 与 live-pusher 使用说明

多端应用中使用 `live-player` 与 `live-pusher` 组件能力是基于[腾讯云直播 SDK](https://cloud.tencent.com/document/product/454) 实现，使用腾讯云直播 SDK 时需配合腾讯云直播服务使用，即需前往腾讯云视立方控制台对直播 License 进行新增和续期等操作，获得`LiveLicenseUrl` 和 `LiveLicenseKey`信息后前往微信开发者工具 `project.miniapp.json` 勾选 Live SDK，并且完成相关配置。

补充：live-player 和 live-pusher 在 App 端使用无需像小程序那样提供资质才能进行开通，按照下方的指南操作即可使用。

## [#](#_1、SDK-版本要求) 1、SDK 版本要求

- iOS SDK：需使用版本号 ≥ 1.6.3
- Android SDK ：需使用版本号 ≥ 1.6.11 (低于该版本的 SDK 仍可使用 live-player 与 live-pusher，但是无法与腾讯云直播服务配合使用，因此建议开发者升级至最新的 SDK )

## [#](#_2、开发者工具版本要求) 2、开发者工具版本要求

- 使用 live-player 和 live-pusher 组件需要勾选 「Live SDK」，如果开发者工具上没看到该扩展 SDK ，请将开发者工具升级到最新，即至少是版本 > 1.06.2505162

## [#](#_3、依赖的扩展-SDK) 3、依赖的扩展 SDK

- Android： XWeb SDK 或 XWeb Embed SDK 以及 Live SDK
- iOS: Media SDK 以及 Live SDK

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202505221225705.png)

## [#](#_4、License-配置步骤) 4、License 配置步骤

- 前往腾讯云控制台按照文档去申请`LiveLicenseUrl` 和 `LiveLicenseKey`，详细操作步骤可查看<https://cloud.tencent.com/document/product/454/34750>
- **【补充说明】如果是 TRTC 服务用的 `<live-player>` 可以不需要 LicenseKey，留空即可**

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202503170957973.png)

- 前往`project.miniapp.json`勾选「Live SDK」并配置`LiveLicenseUrl` 和 `LiveLicenseKey`（注意，Android 和 iOS 都需要配置）

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202505211458293.png)

- 完成上述配置后，即可正常使用[live-player](https://developers.weixin.qq.com/miniprogram/dev/component/live-player.html) 与 [live-pusher](https://developers.weixin.qq.com/miniprogram/dev/component/live-pusher.html)

Incorrect translation.