# [#](#wx-login-mock) wx.login mock

由于在小程序项目中是通过 `wx.login` 进行登录，以及业务上是通过 `openid` 作为用户身份的唯一 id，然而 `wx.login` 在 App 模式下不可用，因此，为了方便开发者将小程序构建为 App 之后，在无需业务后台进行任何调整的情况下可以快速体验完整的 App。开发者工具提供了「wx.login mock」功能可通过 mock 的方式获取非真实用户的 `jscode` 用于测试。

- 即，开发者可在开发者工具中将「wx.login mock」功能开启，然后构建的 App 中运行的 `wx.login` 将返回非真实用户的 `jscode`，如果不开启「wx.login mock」功能，`wx.login` 在 App 的运行环境中调用就会报错。

## [#](#一、前置条件) 一、前置条件

- 开发者工具版本 ≥ 1.06.2406142（建议使用最新的[开发版](https://developers.weixin.qq.com/miniprogram/dev/devtools/log)开发者工具）
- iOS SDK >= 1.3.27
- Android SDK >= 1.3.19

## [#](#二、操作步骤) 二、操作步骤

在微信开发者工具的「工具栏 - 详情 - 本地设置」处勾选「多端应用模式下，启用 wx.login mock 功能」设置，并重新构建即可。

- 注意：开启/关闭「wx.login mock」功能，都需重新构建才会生效。

![](https://res.wx.qq.com/op_res/bCgqLRI8ip9jS96UJpZQIGXuNtudH4mkQ6xjmr5e8_ilInnBhQLub5f3NsUl6xTg4I2Dt43O1GkkJfnaQi4rDA)

### [#](#wx-login-mock-成功的条件) wx.login mock 成功的条件

- 模式为：多端应用模式；版本为：开发版

![](https://res.wx.qq.com/op_res/bCgqLRI8ip9jS96UJpZQIM5lqWNSEdM3w0Sjt7hbhXlt4Ykf0DFYggGCFoeaZf5v2KwHgBV-tiNv2USkVeSp4Q)

- 在开发者工具已开启「wx.login mock」功能
- 开启「wx.login mock」功能后，有重新构建安装包
- 开发者工具需保持登录状态，即如果开发者工具的登录态掉了，也会导致「wx.login mock」失效
- 小程序与多端应用保持绑定的关系，即，如果将小程序和多端应用解除绑定了，也会导致「wx.login mock」失效

### [#](#wx-login-mock-生效优先级) wx.login mock 生效优先级

- 当开发者在多端应用中接入了[小程序登录服务](../../quickstart/auth)，即 `adaptWxLogin` 配置了 `true`（即已配置将 wx.login 自动适配成 wx.getMiniProgramCode），同时又开启了「wx.login mock」功能，「wx.login mock」功能生效优先级更高。

## [#](#三、确认-wx-login-mock-成功或失败) 三、确认 wx.login mock 成功或失败

真机运行时，开发者可将 vconsole 打开查看日志，成功和失败参考如下：

- 如果失败，可以参考日志返回的错误信息进行调整

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202406141507760.png)

Incorrect translation.