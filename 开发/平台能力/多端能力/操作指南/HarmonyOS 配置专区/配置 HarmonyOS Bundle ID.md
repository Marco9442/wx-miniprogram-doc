# [#](#配置-HarmonyOS-BundleId) 配置 HarmonyOS BundleId

Bundle ID (Bundle Identifier) 是 HarmonyOS 应用程序的唯一标识符，字符串形式，由 AppGallery 分配，用于识别应用商店中的应用程序。每个 HarmonyOS 应用都必须有一个唯一的 Bundle ID。因此，基于多端框架开发 HarmonyOS 应用也需为多端应用配置 Bundle ID。

本文内容主要包含基础概念说明以及配置多端应用的 Bundle ID 详细指引

## [#](#基础介绍) 基础介绍

HarmonyOS 应用的包名即为本文中提到的"HarmonyOS BundleId"，开发者需先前往华为官网创建鸿蒙应用并且自定义应用包名，详细操作步骤可查看：<https://developer.huawei.com/consumer/cn/doc/app/agc-help-createharmonyapp-0000001945392297>

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919120852444.png)

- 上图中的【应用包名】需要配置在多端应用控制台中

## [#](#操作指引) 操作指引

### [#](#自定义配置) 自定义配置

- 如果你当前的多端应用未绑定移动应用账号，那么直接点击【修改】，然后选择「自定义配置」，然后保存

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919121131124.png) ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20251118202300380.png) ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20251118202515269.png)

### [#](#复用移动应用账号) 复用移动应用账号

- 如果你当前的多端应用已绑定移动应用账号，那么你需要前往【微信开放平台 - 管理中心 - 移动应用 - 开发信息】中配置鸿蒙的包名信息（注意，移动应用需审核通过）

### [#](#在开发者工具查看-BundleId) 在开发者工具查看 BundleId

- 配置了鸿蒙的包名后，即可在开发者工具中查看到配置的包名

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919121214238.png)

Incorrect translation.