# [#](#基础-SDK) 基础 SDK

## [#](#一、基础介绍) 一、基础介绍

**SDK名称**：小程序多端框架 SDK

**接入文档**：[https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/quickstart/first\_app.html](../../quickstart/first_app)

**iOS SDK 版本号**：[1.6.24](../../changelog/ios/changelog)

**Android SDK 版本号**：[1.6.21](../../changelog/android/changelog)

**HarmonyOS SDK 版本号**：[0.5.4](../../changelog/ohos/changelog)

**SDK介绍**：小程序多端框架 SDK 是一款支持使用微信小程序技术和微信开发者工具开发移动应用的框架，开发者可以一次编码，分别编译为微信小程序和 Android、 iOS 以及 HarmonyOS 应用，实现多端开发的软件开发工具包。

**开发者**：深圳市腾讯计算机系统有限公司

**个人信息处理规则**：[小程序多端框架 SDK 个人信息保护规则](agreement/sdk)

## [#](#二、使用介绍) 二、使用介绍

为了保证 SDK 的安全稳定性以及控制 SDK 体积，将 SDK 拆分为基础 SDK 与扩展 SDK，后者是前者的补充，因此使用扩展 SDK 也必须依赖基础 SDK。其中，扩展 SDK 开发者可以按需在微信开发者工具的 `project.miniapp.json` 中进行配置，即扩展 SDK 为可选项。

基础 SDK 中集成了丰富的 API 与相关组件，用来保障最基础的应用的正常运行，下方 JSAPI 在基础 SDK 中已经包含，即开发者在微信开发者工具的 `project.miniapp.json` 只需要配置对应的 SDK 版本即可。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202401232002187.png)

基础 SDK 收集设备型号及操作系统版本信息，用于解决在不同设备、不同操作系统下 SDK 产品的兼容性问题。

如果开发者的业务逻辑中调用了例如日历、联系人等涉及用户个人信息的 JSAPI，应当在隐私政策中进行声明（点此可查看[个人信息监控范围](personal)）。

## [#](#三、-JSAPI) 三、 JSAPI

基础 SDK 所支持的 JSAPI 如下：

| JSAPI 分组名称 | 接口详情 |
| --- | --- |
| 「基础」相关 API | [「API 总览 - 基础」](../../api/total#%E5%9F%BA%E7%A1%80) |
| 「系统」相关 API | [「API 总览 - 系统」](../../api/total#%E7%B3%BB%E7%BB%9F) |
| 「生命周期」相关 API | [「API 总览 - 生命周期」](../../api/total#%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F) |
| 「应用级事件」相关 API | [「API 总览 - 应用级事件」](../../api/total#%E5%BA%94%E7%94%A8%E7%BA%A7%E4%BA%8B%E4%BB%B6) |
| 「调试」相关 API | [「API 总览 - 调试」](../../api/total#%E8%B0%83%E8%AF%95) |
| 「性能」相关 API | [「API 总览 - 性能」](../../api/total#%E6%80%A7%E8%83%BD) |
| 「路由」相关 API | [「API 总览 - 路由」](../../api/total#%E8%B7%AF%E7%94%B1) |
| 「EventChannel」相关 API | [「API 总览 - EventChannel」](../../api/total#eventchannel) |
| 「界面」相关 API | [「API 总览 - 界面」](../../api/total#%E7%95%8C%E9%9D%A2) |
| 「导航栏」相关 API | [「API 总览 - 导航栏」](../../api/total#%E5%AF%BC%E8%88%AA%E6%A0%8F) |
| 「Tab Bar」相关 API | [「API 总览 - Tab Bar」](../../api/total#tab-bar) |
| 「字体」相关 API | [「API 总览 - 字体」](../../api/total#%E5%AD%97%E4%BD%93) |
| 「滚动」相关 API | [「API 总览 - 滚动」](../../api/total#%E6%BB%9A%E5%8A%A8) |
| 「动画」相关 API | [「API 总览 - 动画」](../../api/total#%E5%8A%A8%E7%94%BB) |
| 「置顶」相关 API | [「API 总览 - 置顶」](../../api/total#%E7%BD%AE%E9%A1%B6) |
| 「自定义组件」相关 API | [「API 总览 - 自定义组件」](../../api/total#%E8%87%AA%E5%AE%9A%E4%B9%89%E7%BB%84%E4%BB%B6) |
| 「菜单」相关 API | [「API 总览 - 菜单」](../../api/total#%E8%8F%9C%E5%8D%95) |
| 「发起请求」相关 API | [「API 总览 - 网络 - 发起请求」](../../api/total#%E5%8F%91%E8%B5%B7%E8%AF%B7%E6%B1%82) |
| 「下载」相关 API | [「API 总览 - 网络 - 下载」](../../api/total#%E4%B8%8B%E8%BD%BD) |
| 「上传」相关 API | [「API 总览 - 网络 - 上传」](../../api/total#%E4%B8%8A%E4%BC%A0) |
| 「进入多端 App」相关 API | [「API 总览 - 监听进入多端 App」](../../api/total#%E7%9B%91%E5%90%ACscheme-universallink%E8%BF%9B%E5%85%A5%E5%A4%9A%E7%AB%AFapp) |
| 「数据缓存」相关 API | [「API 总览 - 数据缓存」](../../api/total#%E6%95%B0%E6%8D%AE%E7%BC%93%E5%AD%98) |
| 「画布」相关API (iOS) | [「API 总览 - 画布」](../../api/total#%E7%94%BB%E5%B8%83) |
| 「富文本」相关 API | [「API 总览 - 媒体 - 富文本」](../../api/total#%E5%AF%8C%E6%96%87%E6%9C%AC) |
| 「文件」相关 API | [「API 总览 - 文件」](../../api/total#%E6%96%87%E4%BB%B6) |
| 「日历」相关 API | [「API 总览 - 日历」](../../api/total#%E6%97%A5%E5%8E%86) |
| 「联系人」相关 API | [「API 总览 - 联系人」](../../api/total#%E8%81%94%E7%B3%BB%E4%BA%BA) |
| 「电量」相关 API | [「API 总览 - 电量」](../../api/total#%E7%94%B5%E9%87%8F) |
| 「剪贴板」相关 API | [「API 总览 - 剪贴板」](../../api/total#%E5%89%AA%E8%B4%B4%E6%9D%BF) |
| 「加密」相关 API | [「API 总览 - 加密」](../../api/total#%E5%8A%A0%E5%AF%86-1) |
| 「屏幕」相关 API | [「API 总览 - 屏幕」](../../api/total#%E5%B1%8F%E5%B9%95) |
| 「键盘」相关 API | [「API 总览 - 键盘」](../../api/total#%E9%94%AE%E7%9B%98) |
| 「电话」相关 API (Android) | [「API 总览 - 电话」](../../api/total#%E7%94%B5%E8%AF%9D) |
| 「加速计」相关 API (Android) | [「API 总览 - 加速计」](../../api/total#%E5%8A%A0%E9%80%9F%E8%AE%A1) |
| 「罗盘」相关 API (Android) | [「API 总览 - 罗盘」](../../api/total#%E7%BD%97%E7%9B%98) |
| 「设备方向」相关 API (Android) | [「API 总览 - 设备方向」](../../api/total#%E8%AE%BE%E5%A4%87%E6%96%B9%E5%90%91) |
| 「陀螺仪」相关 API (Android) | [「API 总览 - 陀螺仪」](../../api/total#%E9%99%80%E8%9E%BA%E4%BB%AA) |
| 「振动」相关 API (Android) | [「API 总览 - 振动」](../../api/total#%E6%8C%AF%E5%8A%A8) |
| 「短信」相关 API (Android) | [「API 总览 - 短信」](../../api/total#%E7%9F%AD%E4%BF%A1) |
| 「Worker」相关 API | [「API 总览 - Worker」](../../api/total#worker) |
| 「WXML」相关 API | [「API 总览 - WXML」](../../api/total#wxml) |

如基础 SDK 未涉及到，需引入[扩展 SDK](extend) ，详情可查看[小程序多端框架扩展 SDK](extend)

## [#](#四、合规指南) 四、合规指南

为帮助使用小程序多端框架 SDK 开发者（以下简称“你”）在符合个人信息保护相关法律法规及标准的规定下合规接入、使用本SDK产品，微信（以下简称"我们"）特制定《小程序多端框架 SDK 开发者合规使用指引》（以下简称“本指引”），便于你使用小程序多端框架 SDK 过程中符合相应的合规要求。请你在接入、使用小程序多端框架SDK前，充分阅读和了解本指引的内容。

### [#](#_4-1-使用最新SDK版本的说明) 4.1 使用最新SDK版本的说明

我们高度重视小程序多端框架SDK的功能优化、个人信息安全和保护，将适时升级迭代SDK版本以提升产品的安全性和稳定性，确保符合相关法律法规及、监管及标准的最新合规要求。强烈建议你升级使用最新版本SDK，以便保障你正常使用SDK最新功能、避免因你更新不及时产生的不利影响（例如APP被通报或下架等）。

SDK 更新后，我们会及时更新 SDK 更新日志，开发者可及时查看：

- [iOS SDK 更新日志](../../changelog/ios/changelog)
- [Android SDK 更新日志](../../changelog/android/changelog)
- [HarmonyOS SDK 更新日志](../../changelog/ohos/changelog)

### [#](#_4-2-APP-隐私政策中应披露第三方-SDK-相关情况) 4.2 APP 隐私政策中应披露第三方 SDK 相关情况

请你确保你开发或运营的 APP 配备了符合监管要求的个人信息处理规则（以下简称《隐私政策》）。请你务必明确告知终端用户你的 APP 集成了第三方SDK服务。你应在《隐私政策》中添加关于本 SDK 收集使用个人信息的目的、方式和范围等，并显示本SDK的开发运营者名称及隐私政策链接。你应在 APP 登录注册页面及 APP 首次运行时，通过弹窗、文本链接及附件等简洁明显且易于访问的方式，应当以清晰易懂的语言告知用户《隐私政策》，由用户在充分知情的前提下，作出自愿明确的意思表示。

### [#](#_4-3-SDK-申请系统权限的说明) 4.3 SDK 申请系统权限的说明

请你确保你开发或运营的 APP 配备了符合监管要求的系统权限的说明，即，应用的隐私政策中需详细描述使用权限的用途，使用说明如下：

- [Android 系统权限配置指南](../../handbook/devtools/auth-message)
- [iOS 隐私信息访问许可描述配置指南](../../handbook/devtools/iOS-auth-message)

### [#](#_4-4-其他注意事项) 4.4 其他注意事项

**1、你接入小程序多端框架 SDK 前的合规自查**

为确保你就本SDK的使用获得终端用户的授权，且遵守个人信息保护要求和合规流程，我们建议你在接入小程序多端框架 SDK前进行合规自查。

（1）请仔细阅读并按本说明文档提示对你APP的《隐私政策》进行合规自查。

（2）请务必做延迟初始化配置，确保获得用户同意后再初始化SDK。

（3）当小程序多端框架 SDK基于最新的法律法规或监管要求进行更新后，请你在收到版本更新通知时及时将你 APP 集成的小程序多端框架 SDK升级到最新版本。

（4）其他国家相关法律法规、监管政策及标准的要求。

**2、以下文件供开发者参考**

（1）[《个人信息保护法》](http://www.npc.gov.cn/npc/c2/c30834/202108/t20210820_313088.html)

（2）[《工业和信息化部关于进一步提升移动互联网应用服务能力的通知》](https://www.gov.cn/zhengce/zhengceku/2023-03/02/content_5744106.htm)

（3）[《工业和信息化部关于开展信息通信服务感知提升行动的通知》](https://www.gov.cn/zhengce/zhengceku/2021-11/06/content_5649420.htm)

（4）[《工业和信息化部关于开展纵深推进APP侵害用户权益专项整治行动的通知》](https://www.gov.cn/zhengce/zhengceku/2020-08/02/content_5531975.htm)

（5）[《工业和信息化部关于开展APP侵害用户权益专项整治工作的通知》](https://www.gov.cn/xinwen/2019-11/07/content_5449660.htm)

（6）[《App违法违规收集使用个人信息行为认定方法》](https://www.cac.gov.cn/2019-12/27/c_1578986455686625.htm)

（7）[《常见类型移动互联网应用程序必要个人信息范围规定》](https://www.gov.cn/zhengce/zhengceku/2021-03/23/content_5595088.htm)

（8）[《GB/T 35273-2020信息安全技术 个人信息安全规范》](https://openstd.samr.gov.cn/bzgk/gb/newGbInfo?hcno=4568F276E0F8346EB0FBA097AA0CE05E&refer=outter)

（9）[《GB/T 41391-2022信息安全技术 移动互联网应用程序（App）收集个人信息基本要求》](https://openstd.samr.gov.cn/bzgk/std/newGbInfo?hcno=977D9EBB32ABF0A7DD6A1215969FE57A)

Incorrect translation.