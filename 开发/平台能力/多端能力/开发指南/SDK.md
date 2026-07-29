# [#](#SDK) SDK

## [#](#一、基本介绍) 一、基本介绍

在微信客户端中运行的小程序项目，API 的实现是由小程序基础库完成的，因为所有的微信客户端中都内置了一个版本的基础库，因此我们的小程序代码包不需要包含这一部分。

当小程序升级为多端 APP，运行在用户设备中时，原来用于实现 API 的基础库就需要跟着多端项目代码一起打包进安装包中。这个基础库即为 SDK。

需要注意，多端项目打包的 SDK 和微信客户端内置的基础库 SDK 是完全不同的。多端框架根据 Android 和 iOS 分别提供了专属 SDK，两个 SDK 的版本独立更新，开发者可以在小程序开发者工具中看到运行时的 SDK 版本，也可以配置指定版本的 SDK。

![](https://mmbiz.qpic.cn/mmbiz_png/PxLPibq1ibyh1W4Ma6ccUa33S5FviayHqCmJth3DhwRbw85MnxmRliaeN0AK0OKs5MsTic8iafMCibDKOMicujibk0o0v6Q/0?wx_fmt=png)

由于 API 涉及到的功能太多，完全打包会严重占用安装包的体积，因此 SDK 这里做了拆分。由一个基础 SDK 和若干个扩展 SDK 组成。

在打包构建时，多端框架会强制打包基础 SDK，集成丰富的 API 与相关组件，用来保障最基础的应用的正常运行。

基础 SDK 支持的 API 列表，请看[此文档](sdk#_2-1-基础-SDK)。

另外针对登录、支付、高级网络、LBS、媒体、蓝牙、苹果登录、消息推送、扫码、画布、广告等场景，延伸出多个扩展 SDK，开发者需要根据自身需要勾选对应的模块。

扩展 SDK 请查看[此文档](extend)

## [#](#二、SDK-信息) 二、SDK 信息

#### [#](#_1-1-iOS-SDK) 1.1 iOS SDK

- **SDK 名称**：小程序多端框架 SDK for iOS
- **接入文档**：[https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/pre-read/sdk/sdk.html](sdk)
- **SDK版本号**：1.6.10
- **SDK介绍**：小程序多端框架 SDK 是一款为开发者提供移动应用构建及运行的相关能力的软件开发工具包
- **开发者**：深圳市腾讯计算机系统有限公司
- **个人信息处理规则**：[《小程序多端框架 SDK 个人信息保护规则》](agreement/sdk)

#### [#](#_1-2-Android-SDK) 1.2 Android SDK

- **SDK 名称**：小程序多端框架 SDK for Android
- **接入文档**：[https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/pre-read/sdk/sdk.html](sdk)
- **SDK版本号**：1.6.7
- **SDK介绍**：小程序多端框架 SDK 是一款为开发者提供移动应用构建及运行的相关能力的软件开发工具包
- **开发者**：深圳市腾讯计算机系统有限公司
- **个人信息处理规则**：[《小程序多端框架 SDK 个人信息保护规则》](agreement/sdk)

## [#](#三、更新日志) 三、更新日志

[iOS SDK 更新日志](../../changelog/ios/changelog)

[Android SDK 更新日志](../../changelog/android/changelog)

Incorrect translation.