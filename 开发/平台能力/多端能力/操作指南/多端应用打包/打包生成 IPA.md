# [#](#打包生成-IPA) 打包生成 IPA

完成「多端应用」的模拟器或真机调试后，开发者可构建 IPA 并安装至 Apple 设备进一步测试，测试完成后亦可构建正式版的 IPA 用于提交 App Store进行审核，审核通过后即可上架。

## [#](#一、开始构建) 一、开始构建

1. 切换到「多端应用模式」，在工具栏中，点击「构建 - 打包生成 IPA」，

![](https://res.wx.qq.com/op_res/hmiQiGmlTRABKGzp5DJV5K12NCugjZrbuZ1xd2P9uj_Idc8uLZK3KSYZ0DBznxLdvJwx0TUKOZLKLqqxJvBT4A)

1. 在弹出的「构建 IPA」面板中完成相关配置

![](https://res.wx.qq.com/op_res/hmiQiGmlTRABKGzp5DJV5BlGJDXiMiXl53XnLvM_w6k8iRAmxjMz6S91r4DX5S_Ew3ACQ1aOIgJX2hyz--R47Q)

## [#](#二、基本信息) 二、基本信息

「构建 IPA」面板中基本信息来源于 `project.miniapp.json` 配置文件，每次构建时会自动拉取配置信息。

![](https://res.wx.qq.com/op_res/hmiQiGmlTRABKGzp5DJV5LU_RTLDhyV4wGo2J70MJVtxqo0flpZqf6gwEBuEVrPm4ZCToR14soMcXwJeHOmiDA)
> 需注意：图标信息根据打包的类型不同，引用不同的配置，请注意分辨。

## [#](#三、Bundle-ID-和-Universal-Link) 三、Bundle ID 和 Universal Link

`Bundle ID` 信息来源于多端应用控制台的配置

- 如创建的多端应用尚未绑定移动应用账号，则默认以平台分配的测试版 `Bundle ID` 构建的 `IPA`。
- 如创建的多端应用已绑定移动应用账号，则以移动应用配置的 `Bundle ID` 和 `Universal Link` 构建 IPA

如需修改`Bundle ID` 信息，点击「去修改」跳转至多端应用控制台修改。具体参考[此文档](../web/bundleid-guide)

## [#](#四、证书配置) 四、证书配置

生成 `IPA` 需使用 `Apple` 证书和 `Profile (mobileprovision)` 文件，相关的配置以及说明如下：

### [#](#_1、临时签名) 1、临时签名

临时签名是指通过 `Apple` 账密自动管理签名证书和 `Profile (mobileprovision)` 文件等文件的生成和使用的方式。主要用于未注册 `Apple` 开发者账号的开发者临时测试使用，无法上架到 `App Store`。

- 适用于免费 `Apple` 账号
- 如果 `Apple AppID (Bundle ID)` 还没注册，会自动注册 `Apple AppID (Bundle ID)` 到登录的 `Apple` 账号
- `Apple AppID (Bundle ID)` 不会开启任何 [capability](https://developer.apple.com/help/account/manage-identifiers/enable-app-capabilities/)（有的 `capability` 并不支持免费账户的 `AppID(Bundle ID)`， 如 `Apple Pay` 和 `In-App Purchase` 等）
- 需要通过 USB 将 iPhone 手机连接到电脑端，会自动注册该设备为该 Apple 账号的信任设备
- 会自动创建签名证书
- 自动生成 `Development` 的 `Profile`。如果该 `Apple AppID (Bundle ID)` 之前已经创建 `Profile`，则会沿用旧的
- 每个应用程序的设备数量限制为 `100` 台
- 每个账号只能创建一个应用程序
- 生成的 `IPA` 无法上架到 `App Store`

### [#](#_2、证书签名) 2、证书签名

证书签名是指通过手动创建管理 Apple 签名证书和 Profile (mobileprovision) 文件，并使用这些文件进行签名的方式。

- 适用于苹果个人账户（收费）/公司账户（收费）
- 可以按照[文档](../certificate/ios)注册 Apple AppID (Bundle ID)、创建证书和生成 Profile(mobileprovision) 文件等
- 使用苹果 Development 和 Ad-hoc 证书构建的产物可用于开发测试
- 使用苹果分发证书构建的产物可用于[上架 App Store](ios-publish)

**如果构建的 IPA 要提交到苹果进行审核以及发布，需选择「证书签名」的方式，且构建的资源包类型要选择「正式版」**

在构建时选「证书签名」且「使用分发证书」时，会需要设置 `Certificate`(P12 文件) 和 `Provisioning Profile` 文件，以及 `Certificate`(P12 文件) 的证书密码。

> 如不知道如何获得 `Certificate`(P12 文件) 和 `Provisioning Profile` 文件，请参考[iOS 证书申请与配置](../certificate/ios)的第三、四部分。

#### [#](#_1-P12证书) (1) P12证书

参考[此步骤文档](../certificate/ios#_3-3-%E5%AF%BC%E5%87%BA-P12) 导出的 p12 文件。

> 需注意该文件需在项目目录下，建议创建一个单独的目录统一存放。

#### [#](#_2-P12密码) (2) P12密码

在导出 `p12` 文件时设置的密码，这个操作在你的本机中完成。

#### [#](#_3-Profile) (3) Profile

参考[此步骤文档](../certificate/ios#%E5%9B%9B%E3%80%81%E5%88%9B%E5%BB%BA-Provisioning-Profile) 创建下载 `mobileprovision` 文件。

#### [#](#_4-签名证书名) (4) 签名证书名

直接填写 `P12` 证书名称后**括号里**的内容。

![](https://res.wx.qq.com/op_res/hmiQiGmlTRABKGzp5DJV5AjCz-9J17gYE4qMLtNEeZvyBoLYZJd_XY8hC3rv_ODBYht44xJyfkE6vfDBoHuQAg)

## [#](#五、资源包配置) 五、资源包配置

资源包的类型分别有：正式版、开发版、开发版（支持远程调试）以及开发版（支持热更新），关于这几个版本的区别以及应用场景可查看[版本介绍](../test/package)

## [#](#六、应用版本配置) 六、应用版本配置

应用版本信息来源于 `project.miniapp.json` 配置文件，每次构建时会自动拉取配置信息。

![](https://res.wx.qq.com/op_res/hmiQiGmlTRABKGzp5DJV5HIwddb8uvpEn2xo8tMq_BC8Ae6K75CMkDzsEYk99dYutpRTjjgq-Cg_AXPW0QqS-Q)

## [#](#七、命令行构建) 七、命令行构建

开发者可以使用命令行构建的方式构建 `IPA`。

开发者**需要将开发者工具升级至最新版 nightly**，并先按照[开发者工具命令行使用文档](https://developers.weixin.qq.com/miniprogram/dev/devtools/cli)准备执行命令的环境，以及查看基础的用法。

按照如下步骤操作：

1. 仔细阅读命令行的使用文档，根据文档执行 `cli open --project` 打开对应的项目。
2. 没有登录需要 `cli login` 登录
3. 成功进入项目后，执行 `cli build-ipa`。

支持参数如下（对齐工具构建面板）：

| 参数名 | 功能说明 | 是否必填 | 参数类型 |
| --- | --- | --- | --- |
| project | 项目路径，需要为系统绝对路径 | 是 | string |
| output | 构建产物的保存路径，需要为系统绝对路径 | 是 | string |
| isDistribute | 是否使用分发证书 | 否 | boolean |
| isRemoteBuild | 是否启用远程构建（必须使用分发证书的情况下才能使用） | 否 | boolean |
| profilePath | profile 文件地址，文件格式为 mobileprovision，相对项目根路径的相对路径 | 否(使用分发证书时必填) | string |
| certificateName | 签名证书名 | 否(使用分发证书时必填) | string |
| p12Path | p12 文件路径，文件格式为 p12，相对项目根路径的相对路径 | 否(使用远程构建时必填) | string |
| p12Password | p12 密码 | 否(使用远程构建时必填) | string |
| tpnsProfilePath | tpnsProfile 文件路径，相对项目根路径的相对路径 | 否 | string |
| isUploadBeta | 是否上传内测版（不使用分发证书时才可使用） | 否 | boolean |
| isUploadResourceBundle | 是否上传资源包 | 否 | boolean |
| resourceBundleVersion | 资源包版本号 | 否 | string |
| resourceBundleDesc | 资源包项目备注 | 否 | string |
| versionName | 应用版本名称 | 否 | string |
| versionCode | 应用版本号 | 否 | number |
| versionDesc | 应用描述 | 否 | string |

证书签名示例：

```
/Applications/wechatwebdevtools.app/Contents/MacOS/cli build-ipa --project /Users/test/project/miniprogram/mini-1 --output /Users/test/Downloads --isDistribute true --isRemoteBuild false --profilePath distribute/distribute_com_tencentdonutminiapp_db.mobileprovision --certificateName 'XIAO TU (AN99464A2B)' --p12Path distribute/distribute.p12 --p12Password 123456 --tpnsProfilePath '' --isUploadBeta false --isUploadResourceBundle false --resourceBundleVersion '' --resourceBundleDesc '' --versionName 0.0.66 --versionCode 103 --versionDesc 一个简单的备注
```

云构建示例：

```
/Applications/wechatwebdevtools.app/Contents/MacOS/cli build-ipa --project /Users/test/project/miniprogram/mini-1 --output /Users/test/Downloads --isDistribute true --isRemoteBuild true --profilePath distribute/distribute_com_tencentdonutminiapp_db.mobileprovision --certificateName 'XIAO TU (AN99464A2B)' --p12Path distribute/distribute.p12 --p12Password 123456 --tpnsProfilePath '' --isUploadBeta false --isUploadResourceBundle false --resourceBundleVersion '' --resourceBundleDesc '' --versionName 0.0.66 --versionCode 103 --versionDesc 一个简单的备注
```

Incorrect translation.