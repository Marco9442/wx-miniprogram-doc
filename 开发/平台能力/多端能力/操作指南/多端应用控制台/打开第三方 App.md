# [#](#打开第三方-App) 打开第三方 App

开发者可通过 [wx.miniapp.openUrl](../../api/miniapp/openUrl) 接口打开第三方 App，但需跳转的目标 App 需在多端控制台进行配置，相关的使用说明如下。

如果开发者是通过 webview 内嵌的 H5，在 H5 中涉及了跳转第三方 App，那么需跳转的目标 App 也是需在多端控制台进行配置。

补充：默认已支持打开浏览器，即 App 中的网页亦可通过 [wx.miniapp.openUrl](../../api/miniapp/openUrl) 接口唤起系统浏览器的方式打开，无需在控制台做相关配置。

![](https://res.wx.qq.com/op_res/QKkyFUByaw2__Forw59yKQp3C4fLp3wC5Egd6wiX3SfQRylJ73H7Y5dPdgM194Y0o-R04bbe8JD6XZaiFfoitw)

### [#](#一、使用说明) 一、使用说明

通过 [wx.miniapp.openUrl](../../api/miniapp/openUrl) 打开第三方 App 或者是通过 webview 内嵌 H5 方式打开第三方 App，都需在多端应用控制台中配置第三方 App 的 Scheme，而当前仅支持打开已经在 App Store 上架的第三方应用。

**其他补充：**

- 这里指的是第三方的 App 要上架 App Store，即，如果要跳转的 App 没有上架 App Store，则无法配置。
- 这里并不是指开发者的多端 App 要上架 App Store。
- 配置好之后，Android 的多端应用亦可使用该接口打开第三方 App。

**其他注意事项：**

- 使用 [wx.miniapp.openUrl](../../api/miniapp/openUrl) 时需按文档要求配置最新 SDK 以及开发者工具。

### [#](#二、操作指引) 二、操作指引

1、添加 App，配置第三方 App 的 URL Scheme。

![](https://res.wx.qq.com/op_res/QKkyFUByaw2__Forw59yKRlHQMCLraObtiziSAyTrWcJrqKsIAGJIfpy1x_lSmR10cUBnpO_44SPFe5JnJ081Q)

2、应用下载地址：当前仅支持填写已经在 App Store 上架的应用的下载地址，并且格式需严格按照「 https://apps.apple.com/cn/app/%E5%BE%AE%E4%BF%A1/id414478124 」。

3、如何获得该格式的下载地址，可查看文档[获取 AppStore 下载地址](https://developers.weixin.qq.com/doc/oplatform/Mobile_App/guideline/getioslink)。

4、填写的 URL Scheme 需按照形如 "weixin://" 的格式填写，否则无法提交成功。

5、URL Scheme 配置后，可调用 wx.miniapp.openUrl 打开第三方 App，该接口的 url 参数的 Scheme 的前缀需与在控制台配置的一致。

Incorrect translation.