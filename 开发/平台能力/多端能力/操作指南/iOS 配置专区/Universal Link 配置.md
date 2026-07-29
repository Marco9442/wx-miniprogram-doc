# [#](#Universal-Link-配置) Universal Link 配置

## [#](#一、介绍) 一、介绍

`Universal Link` 是 Apple 在 iOS 9 推出的一种能够方便的通过传统 HTTPS 链接来拉起 APP 的功能

如果你的 App 支持 Universal Link，那么用户点击这个链接时可以跳转到你的网站并获得无缝重定向到对应的 APP，且不需要通过 Safari 浏览器。如果你的应用不支持的话，则会在 Safari 中打开该链接。

基于多端框架开发 iOS 应用的 Bundle ID 和 Universal Link 均是来源于微信开放平台的移动应用，即在创建移动应用的时候开发者需填写 Bundle ID 和 Universal Link，本文将解释移动应用 Universal Link 的用途以及相关验证方式。

## [#](#二、配置指南) 二、配置指南

- 如果多端应用绑定了移动应用，那么多端应用的 Universal Links 是来源于微信开放平台移动应用配置的 Universal Links，但是由于微信开放平台移动应用只支持配置一个 Universal Links，因此需要配置多个 Universal Links 的情况下，需要在开发者工具的 project.miniapp.json 中配置 `universalLink`，如下图：
- 如果端应用不绑定移动应用，那么直接在开发者工具的 `project.miniapp.json` 中配置 `universalLink`，如下图：
- 如果在开发者工具中找不到 `universalLink` 这个配置，原因则是工具的版本较低，需要升级至最新的 nightly 开发者工具
- 此外，如需配置多个 universal link，可以使用英文逗号分隔开，例：https://www.xx.com,https://www.xxx.com,https://www.xxxx.com

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202504251414921.png)

## [#](#三、其他说明) 三、其他说明

### [#](#_3-1-为什么需要配置-Universal-Link) 3.1 为什么需要配置 Universal Link

如果你的 iOS 应用无需用到微信能力（如微信分享、微信登录、微信支付等），那么，可以随便配置 Universal Link 都可以，即无需填写一个真正可用的 Universal Link

反之，如果你的 iOS 应用用到微信能力（如微信分享、微信登录、微信支付等），那么，就必须配置一个可用的 Universal Link，确保从你的 App 跳到微信 App 后可以正常返回你的 App。

### [#](#_3-2-如何验证配置的-Universal-Links-是有效的) 3.2 如何验证配置的 Universal Links 是有效的

微信使用第三方 App 的 Universal Links 唤起第三方 App 时，会在 Universal Links 末尾拼接路径和参数，因此开发者 Universal Links 配置必须加上通配符，并测试 Universal Links 拼接字符串能否唤起 App

建议 Universal Links 配置 path，例如 /app/\*，避免全域命中 Universal Links 跳转

按照上面的规则完成配置后，可通过下方的方式验证是否生效

#### [#](#_3-2-1-在-Safari-输入-Universal-Links-包括完整路径-随机字符串-例如-abc) 3.2.1 在 Safari 输入 Universal Links(包括完整路径)+随机字符串(例如: abc)

例如以 `https://help.wechat.com/sdksample/` 为例子，

在 Safari 的 Universal Links：`https://help.wechat.com/sdksample/abc`

#### [#](#_3-2-2-下拉页面检查是否有打开-app-的入口提示-如下图) 3.2.2 下拉页面检查是否有打开 app 的入口提示(如下图)

![](https://res.wx.qq.com/op_res/LIP8n0ettnbQjXVELUmLx-T2iMXF8oZPcwgD2248WJWNm0X6QYEQ_3kgq7r28WxC)

### [#](#_3-3-如果-Universal-Links-失效了会有什么影响) 3.3 如果 Universal Links 失效了会有什么影响

当用户首次使用微信发起分享时，将会出现如下交互流程：从 App 拉起微信-出现「正在连接」页面-返回 App-重新打开微信。以上是新的安全验证流程，每个用户在首次使用时会出现上述跳转\*\*

![](https://res.wx.qq.com/op_res/y0pPDN_HPoNM7hzdSg0TpYHOUpE0hdrjMDp0npt9uJGOVIGtPZJhs1nLHilL2uiW)

然而非首次分享也都一直出现了二次跳转的行为，则是微信 App 这边无法通过开发者的 App 提供的 Universal Links 返回导致，也就是说开发者在移动应用配置的 Universal Links 不生效了，需按照上述步骤 2 的指引检查 Universal Links 配置\*\*

Incorrect translation.