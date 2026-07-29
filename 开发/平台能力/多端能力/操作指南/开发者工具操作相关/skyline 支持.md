# [#](#Skyline-渲染引擎) Skyline 渲染引擎

多端 SDK 支持 Skyline 渲染引擎，开发者可通过目前开放的 Beta 版本结合下方教程指引来进行体验。

- 该功能要求：Android SDK >= 1.2.0；iOS SDK >= 1.2.5（建议使用最新的 SDK）

## [#](#一、准备工作) 一、准备工作

请先将你的小程序代码适配 Skyline 渲染引擎，可查看 [Skyline 渲染引擎官方文档](https://developers.weixin.qq.com/miniprogram/dev/framework/runtime/skyline/introduction)。

## [#](#二、开启体验) 二、开启体验

1、先将工具升级到[最新 nightly 版本](https://developers.weixin.qq.com/miniprogram/dev/devtools/log)。

2、在 project.miniapp.json 文件中勾选 Android 或 iOS 中的 Skyline SDK。

- Android 中使用 Skyline 需要同时勾选 XWeb 模块。

3、重新打包生成 IPA 或者 APK 即可。

![](https://res.wx.qq.com/op_res/jDgvj5ZXKqLKV70G6DMGQPgLfgwpZpFvxebmXJO-wbiv24u8fSFXEbhJQrOeSAMGoSqkZEaqCQHhqXOj2b-J2A) ![](https://res.wx.qq.com/op_res/jDgvj5ZXKqLKV70G6DMGQEdHvN43wLjnfCBE-Kp0iLsSPiWwEnEsWFGaa0TgC9uSyf0wJ1RUQt5iRCI_uGhiCw)

## [#](#三、确认效果) 三、确认效果

可以通过以下方式确认应用已支持 Skyline 渲染功能：

将 vConsole 功能打开，vConsole 按钮上会展示当前页面的渲染类型，如果是 Skyline 类型的页面，则会有 Skyline 标识。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202311021852287.png)

Incorrect translation.