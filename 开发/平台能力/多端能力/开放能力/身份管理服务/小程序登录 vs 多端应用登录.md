# [#](#小程序登录-vs-多端应用登录) 小程序登录 vs 多端应用登录

- [小程序登录](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/login)

  1. 小程序调用 [wx.login](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/login/wx.login.html)，获取到 code 并传递到开发者服务器。
  2. 开发者服务器调用[小程序登录凭证校验](https://developers.weixin.qq.com/miniprogram/dev/server/API/user-login/api_code2session)，获取到 openid、unionid 等信息，开发者可基于该信息构建自定义登录态。
- 多端应用登录

  1. 多端应用调用 JSAPI [wx.weixinAppLogin](../../api/auth/wx.weixinAppLogin)、[wx.weixinMiniProgramLogin](../../api/auth/wx.weixinMiniProgramLogin)、[wx.phoneSmsLogin](../../api/auth/wx.phoneSmsLogin)、[wx.appleLogin](../../api/auth/wx.appleLogin)等)，获取到 code 并传递到开发者服务器。
  2. 开发者服务器调用 [登录凭证校验](../../openapi/code2Verifyinfo)，获取到登录信息 (登录方式、登录时间等) 和用户标识信息 (openid、unionid、手机号、苹果 id 等)，开发者可基于该信息构建自定义登录态。

Incorrect translation.