# [#](#多端应用-Bundle-ID-配置) 多端应用 Bundle ID 配置

Bundle ID (Bundle Identifier) 是 iOS 应用程序的唯一标识符，字符串形式，由 Apple 分配，用于识别应用商店中的应用程序。每个 iOS 应用都必须有一个唯一的 Bundle ID。因此，基于多端框架开发 iOS 应用也需为多端应用配置 Bundle ID。

本文内容主要包含基础概念说明以及配置多端应用的 Bundle ID 详细指引

## [#](#一、基础概念) 一、基础概念

### [#](#_1-1-测试版-Bundle-ID) 1.1 测试版 Bundle ID

多端应用的 Bundle ID 来源于微信开放平台移动应用配置 iOS 开发信息，然而在开发者尚未将多端应用与移动应用进行绑定时，平台为了方便开发者的构建与测试，将默认为每个多端应用分配 `com.tencent.devtoolssaaademo.db` 作为「默认的测试版 Bundle ID」

开发者工具中构建 IPA 或将在「运行于真机」时将以此「默认的测试版 Bundle ID」构建，开发者可在下方查看「默认的测试版 Bundle ID」

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312091426738.png)

上述路径分别为：

- [微信开发者平台](https://developers.weixin.qq.com/platform/) - 多端应用 - 详情 - 移动应用信息；
- 微信开发者工具 - 多端应用模式 - 构建 - 打包生成 IPA

### [#](#_1-2-多端应用的-Bundle-ID) 1.2 多端应用的 Bundle ID

- 如果多端应用绑定了移动应用账号，那么多端应用的 Bundle ID 同步于微信开放平台移动应用，因此，在多端应用绑定了移动应用账号的情况下，如果开发者需自定义 iOS 应用的 Bundle ID，需前往「微信开放平台-管理中心-移动应用」进行修改并提交审核，待审核通过即可同步到多端应用。
- 如果多端应用未绑定移动应用账号，那么多端应用的 Bundle ID 可在多端应用的控制台直接修改即可

#### [#](#规则说明) 规则说明

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202504222107395.png)

- 「复用移动应用账号」的包名和 Bundle ID 信息与「自定义配置」这两种方式是互斥的，不能同时使用，但是可以随时更换
- 例如，如果开发者选择了「复用移动应用账号」，如果需要选择「自定义配置」，那么需要将移动应用账号解绑了（但是，解绑的瞬间会影响已构建的安装包的使用，需要马上就将 Bundle ID 配置回去）
- 如果开发者选择了「自定义配置」，如果需要选择「复用移动应用账号」，那么只需要将移动应用账号绑定即可，绑定后就会将移动应用账号的 Bundle ID 信息覆盖已经配置的 Bundle ID 信息（即，如果移动应用的 Bundle ID 信息和已配置的 Bundle ID 信息不一致的话，更换了之后也会影响已构建的安装包的使用，开发者需注意）

**即，APP 运行启动的时候会检验构建安装包的时候后台配置的 Bundle ID 信息与当前配置的 Bundle ID 信息是否一致，如果不一致，则会启动失败。因此，开发者在进行 Bundle ID 变更的时候务必要知晓相关风险。**

**补充说明**

- 使用默认测试版 Bundle ID 构建的 IPA 只可用于测试体验，不可用于上架应用市场
- 使用开发者自定义正式版 Bundle ID 构建的 IPA 可用于提交至应用市场进行审核和上架

## [#](#二、操作步骤) 二、操作步骤

### [#](#_2-1-前置步骤：在-Apple-Developer-平台定义-Bundle-ID) 2.1 前置步骤：在 Apple Developer 平台定义 Bundle ID

使用 Apple 开发者账号登录 [Developer 控制台](https://developer.apple.com/account)，前往「证书、标识符和描述文件」进入「标识符」页面，开始定义 Bundle ID，具体请参考[此文档](../certificate/ios#%E5%9B%9B%E3%80%81%E5%88%9B%E5%BB%BA-Provisioning-Profile)。

### [#](#_2-2-自定义-Bundle-ID-的操作步骤) 2.2 自定义 Bundle ID 的操作步骤

- 点击「修改」，选择「自定义配置」

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202504222119122.png) ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202504222101922.png)

- 然后，填入在步骤 2.1 自定义的 Bundle ID 信息，点击确定即可

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202504222102337.png)

**注意**

- iOS Bundle ID 和 Android 包名不可以同时为空
- 且 Bundle ID 不可再使用官方分配的测试版 Bundle ID "com.tencent.devtoolssaaademo.db"

### [#](#_2-3-Bundle-ID-同步于移动应用的操作步骤) 2.3 Bundle ID 同步于移动应用的操作步骤

前往[微信开放平台](https://open.weixin.qq.com/)创建移动应用账号，并配置 iOS 开发信息

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312091451957.png)

特别说明：此时填入的 Bundle ID 不可填平台默认分配的 `com.tencent.devtoolssaaademo.db`，需填入 2.1 步骤中自定义的 Bundle ID

详细的移动应用创建指引可查看[复用多端应用快速创建移动应用](mobile_app)或[直接创建移动应用](open_application_create)

#### [#](#_2-3-1-在多端应用控制台绑定移动应用) 2.3.1 在多端应用控制台绑定移动应用

参考 2.3 创建并配置移动应用后，待移动应用审核通过后，即可前往 [微信开发者平台](https://developers.weixin.qq.com/platform/)，将移动应用与多端应用进行绑定。

操作路径为：多端应用 - 详情 - 移动应用配置 - 立即绑定移动应用账号

![](https://res.wx.qq.com/op_res/qu4BW3-JYa-KlWfAdFqtla8DCR0ChEkStUqLbqmmg5LI6x-29-03HKLo8Y0U_YbaUpMPJb7IVeuL82xdLv4_dg)

补充：在微信开发者平台**绑定**移动应用的详细指引可查看：[绑定移动应用账号](application_create)

#### [#](#_2-3-2-配置后呈现效果) 2.3.2 配置后呈现效果

完成 Bundle ID 的配置后，多端应用控制台与微信开发者工具的呈现效果如下图所示：

|  |  |
| --- | --- |
|  |  |

|  |  |
| --- | --- |
|  |  |

#### [#](#_2-3-3-配置后呈现效果) 2.3.3 配置后呈现效果

- 移动应用绑定于多端应用后，开发者配置的 Bundle ID 等开发信息将从微信开放平台同步到开发者工具，此时构建的 IPA 是基于开发者配置的正式版 Bundle ID，构建 IPA 的详细指引可查看：[打包生成 IPA](../build/build-ipa)

Incorrect translation.