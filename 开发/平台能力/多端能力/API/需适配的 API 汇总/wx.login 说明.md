# [#](#小程序登录-wx-login-说明) 小程序登录 (wx.login) 说明

- 在微信小程序中使用 [wx.login](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/login/wx.login.html) 即可实现登录，但该接口在 App 中不适用
- App 的登录方式，一般是手机号登录、微信登录等。
- 而微信小程序的登录方式，一般是在小程序端调用 `wx.login` 获取 `code`，然后在服务端验证的方式来实现登录。
- 基于此背景，平台新增提供 `wx.weixinMiniProgramLogin` 和 `wx.getMiniProgramCode` 作为多端应用适配小程序登录方案
- 关于这两个接口的试用场景可查看[小程序登录适配方案说明](../../new-capability/auth/loginCompatible)

Incorrect translation.