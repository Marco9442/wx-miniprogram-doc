# [#](#iOS-证书申请与配置) iOS 证书申请与配置

**如你不想手动进行证书申请，可以选择使用[证书自动管理](ios-mgnt)。**

## [#](#一、概述) 一、概述

当你运行到 iOS 系统真机或生成 iOS 的安装包，需使用 `Apple` 证书和 `Profile` (`mobileprovision`) 文件进行签名，有两种方式：

## [#](#_1-1-临时签名) 1.1 临时签名

临时签名是指通过 Apple 账密，来自动管理签名证书和 `Profile` (`mobileprovision`) 等文件的生成和使用。微信开发者工具内部直接集成了相应的工具，可以无需 `Apple` 开发者账号注册，就可以获取临时签名，有一定的限制和时效性，仅用于测试。

- 适用于免费 `Apple` 账号
- 需要通过 `USB` 将 `iPhone` 手机连接到电脑端，会自动注册该设备为该 `Apple` 账号的信任设备
- 如果 `Apple AppID` (`Bundle ID`) 还没注册，会自动注册 `Apple AppID` (`Bundle ID`) 到该 `Apple` 账号
- `Apple AppID` (`Bundle ID`) 不会开启任何 [capability](https://developer.apple.com/help/account/manage-identifiers/enable-app-capabilities/)（有的 `capability` 并不支持免费账户的 `AppID`(`Bundle ID`)，如 `Apple Pay` 和 `In-App Purchase` 等）
- 会自动创建签名证书
- 自动生成 `Development` 的 `Profile`。如果该 `Apple AppID` (`Bundle ID`) 之前已经创建 `Profile`，则会沿用旧的
- 每个应用程序的设备数量限制为 100 台
- 每个账号只能创建一个应用程序
- 生成的 IPA 无法上架到 App Store

![](https://res.wx.qq.com/op_res/nw0yXao5eKwmuJAr1D4qLDHNHD0ok0f43m5hIE3qnM5zpl48cAuTBs4H-FfhV4RLYPCILmKj3DYK8sSNHXkDPQ)

当你选择临时签名进行真机运行和构建安装包，需要通过 USB 将 iPhone 手机连接到电脑端，在「运行」和「构建」后会出现弹窗，需填写连接的设备所登录的苹果账号和密码（注意：非苹果开发者账号）

![](https://res.wx.qq.com/op_res/nw0yXao5eKwmuJAr1D4qLFeBiQQKg3D3DXvTwFmFY3GKPHLsLkAo4X4wp5fIyS2RxTQJGoIspts3vBZSn0u4cw) ![](https://res.wx.qq.com/op_res/nw0yXao5eKwmuJAr1D4qLHNV6aUhDQImUvq-14Gk9Yj80rQXkyAGRclcJuEzNJol-Hog6hdasQlDz_KQ7kzzgw)

开发者可选择是否记住账号，如果选择记住账号，则下次运行点击「运行」或「构建」不再出现上述弹窗；反之，则每次点击「运行」和「构建」都会出现。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202307110035228.png)

## [#](#_1-2-证书签名) 1.2 证书签名

证书签名是指在 Apple 开发者账号中，自行创建和管理 Apple 签名证书和 Profile (mobileprovision) 文件，并使用这些文件进行签名。

- 适用于苹果个人账户（收费）/公司账户（收费）
- 使用苹果 Development 和 Ad-hoc 证书构建的产物可用于开发测试
- 需自行注册 Apple AppID (Bundle ID)、创建证书和生成 Profile(mobileprovision) 文件等
- 使用苹果分发证书构建的产物可用于上架 App Store

![](https://res.wx.qq.com/op_res/nw0yXao5eKwmuJAr1D4qLCaxmb7rGNqJiF2eb797f7sDQ6I04i3sKgP-ycArHzkci-b03cSJfzIRMe9FzhMz6A)

证书签名需先申请证书，当运行至真机选「证书签名」时，或者在构建时选「证书签名」且「不使用分发证书」，过程中会弹出如下弹窗，你需要上传相关文件信息和填写密码。关于证书如何申请，请阅读本文后续章节。

![](https://res.wx.qq.com/op_res/nw0yXao5eKwmuJAr1D4qLKH0IBm8iAe5kTkiCmvviRsV0bObMZueB_RXZLIJE1FplwdpAGgPEpF3ZVdzIvdRpQ)

## [#](#_1-3-配置管理) 1.3 配置管理

iOS 签名证书的应用场景有如下：

- 在微信开发者工具运行于 iOS 模拟器和真机前需配置证书项目信息
- 在微信开发者工具构建 IPA 时需配置证书项目信息

使用上述功能时，首先会出现 iOS 签名证书管理，后续如需对签名进行修改可在「工具栏 - 选择设备 - iOS 签名证书管理」进行管理。（构建直接在构建时弹窗中确认，无需在此单独配置）

![](https://res.wx.qq.com/op_res/nw0yXao5eKwmuJAr1D4qLIkVihHzzBYbBsUYg8jSCfRiPnQn3B_LcavYz2V2MJKptxQW9g4N79R1V-r4PSZKpQ)

## [#](#_1-4-清除缓存) 1.4 清除缓存

开发者在证书弹窗时，如选择记住账号，则下次运行点击「运行」或「构建」不再出现弹窗。而如果你忘记「上一次」的配置是什么或者需要修改「上一次」的配置，可前往「工具栏 - 清缓存 - 清除签名缓存」进行操作

![](https://res.wx.qq.com/op_res/XlY0EIeaC5LicodY_mKyt3fmNZz2odYNeHGBFwj42FHPnEBpWd-CDbuXJQv-uncf5U5CeWOFwqks4sZ29csXAg)

开发者可按需选择清除「清除 iOS 临时签名缓存」和「清除 iOS 证书签名缓存」

## [#](#二、iOS-证书相关概念) 二、iOS 证书相关概念

由于你需自行注册 Apple 开发者账号和完成证书申请过程，因此需对 Apple 证书具备一定概念。

### [#](#_2-1-苹果开发者账号) 2.1 苹果开发者账号

创建 iOS 证书和 Profile 需使用付费的苹果账号，苹果开发者账号有三种：个人开发者、公司开发者、企业开发者，用途各有不同。

- 个人开发者和公司开发者是 99 美刀/年，企业开发者是 299 美刀/年。
- 企业开发者一般是大企业开发内部应用时使用，不能上架 App Store 的。

**请先确保你已经有「个人开发者」或「公司开发者」账号！**

### [#](#_2-2-证书介绍) 2.2 证书介绍

证书有多种类型，用于不同的目的。以下是 iOS 证书的分类：

- **开发者证书（Developer Certificate）：** 用于在开发阶段对应用程序进行签名和调试。开发者证书由苹果开发者中心颁发，需要使用 Xcode 或者其他开发工具进行申请和管理。
- **分发证书（Distribution Certificate）：** 用于将应用程序分发给其他用户或者上传到 App Store 进行审核。分发证书由苹果开发者中心颁发，需要使用 Xcode 或者其他开发工具进行申请和管理。
- **推送证书（Push Certificate）：** 用于实现远程推送功能，可以让应用程序接收来自服务器的推送通知。推送证书由苹果开发者中心颁发，需要使用 Xcode 或者其他开发工具进行申请和管理。
- **企业证书（Enterprise Certificate）：** 用于将应用程序分发给企业内部员工或者客户。企业证书由苹果开发者中心颁发，需要使用 Xcode 或者其他开发工具进行申请和管理。

不同的证书用于不同的场景和阶段，请妥善保存和归类各种证书，避免串用。

### [#](#_2-3-Provisioning-Profile-介绍) 2.3 Provisioning Profile 介绍

配置文件（Provisioning Profiles）同样也分两种，分为开发（Development）和发布（Distribution），配置文件中包含了证书、App ID、设备（Devices），后缀名为 .mobileprovision。它在开发者账号体系中扮演着配置和验证的角色，是真机调试和打包上架必须的文件。

- 一个 `Provisioning Profile` 对应一个 `App ID`（`bundleId`）
- `Provisioning Profile` 决定 Xcode 用哪个证书（公钥）/私钥组合（`Key Pair/Signing Identity`）来签名应用程序（`Signing Product`），将在应用程序打包时嵌入到 .ipa 包里。
- `Provisioning Profile` 把这些信息全部打包在一起，方便我们在调试和发布程序打包时使用。这样，只要在不同的情况下选择不同的 `Provisioning Profile` 文件就可以了。
- `Provisioning Profile` 也分为 `Development` 和 `Distribution` 两类，有效期同 `Certificate` 一样。
  - `Development` 版本的 `ProvisioningProfile` 用于开发调试。
  - `Distribution` 版本的 `ProvisioningProfile` 主要用于提交 `App Store` 审核，其不指定开发测试的 `Devices`。

### [#](#_2-4-总结) 2.4 总结

在「微信开发者工具」中打包 iOS 应用的安装包（ipa）时，主要需要 `Certificate` 和 `Provisioning Profile` 两个文件，以及 `Certificate` 的证书密码。

![](https://res.wx.qq.com/op_res/nw0yXao5eKwmuJAr1D4qLKH0IBm8iAe5kTkiCmvviRsV0bObMZueB_RXZLIJE1FplwdpAGgPEpF3ZVdzIvdRpQ)

## [#](#三、生成-iOS-Certificate) 三、生成 iOS Certificate

**`Windows` 系统不支持，创建证书只能在 `macOS` 完成，因此本章节教程仅适用于 Mac 系统**

### [#](#_3-1-创建-CSR-文件（证书请求文件）) 3.1 创建 CSR 文件（证书请求文件）

1. 进入 macOS，打开「钥匙串」，点击「钥匙串访问 -> 证书助理 -> 从证书颁发机构请求证书」

![](https://res.wx.qq.com/op_res/GIW9qpUZ3UpNuH8YiCxmzrkX0B7oyTqkcJhq_qeLcwsLkMKJJ8qrhilvOqZ1mHSBjVOFGPkgdFz9ZNvQYFQ-bQ)

2. 按照图示，填写对应的信息，Keychain 将生成一个包含开发者身份信息的 CSR（Certificate Signing Request）文件，Keychain Access->Keys（密钥）中会增加一对 Public/Private Key Pair。

![](https://res.wx.qq.com/op_res/GIW9qpUZ3UpNuH8YiCxmzv8qu6QNfnQu4mL6RqOyWrK9EgGLJsQSyhp2rWiTerN6iCxzXTNysfVIZqQsIM8hFg)

3. 当选择「存储到磁盘」时，会提醒保存至本地，保存后的文件应该是下图所示类型。

![](https://res.wx.qq.com/op_res/GIW9qpUZ3UpNuH8YiCxmzlQJmr7_wRNajtsFmX7rHUyF6_9GOcP0q2oKErcxXeceBwYkfnZj7dveE_HGvxjCAA)

### [#](#_3-2-创建-Certificates) 3.2 创建 `Certificates`

1. 使用 Apple 开发者账号登录 [Developer 控制台](https://developer.apple.com/account)，前往「证书、标识符和描述文件」进入「证书」页面。

> 没有 Apple 开发者账号需要先注册并认证账号为可用，否则接下来的步骤完成不了。

![](https://res.wx.qq.com/op_res/GIW9qpUZ3UpNuH8YiCxmzgH1Qwg-_OQgsT_iTAli9A_3-iU7wFfxLPs8u4a1qMS6BBB9HBAeILdjaS4BCXZj5w)

2. 点击 `Certificates` 后的「+」号，进入 `Create a New Certificate` 环节

![](https://res.wx.qq.com/op_res/GIW9qpUZ3UpNuH8YiCxmzr8hfnKM-ZpHblujdb4klUr3nJ2pGVSr9JWw22G335jFibBKOYRploHXpiotj6rAlw)

3. 根据自己的需要选择 `Apple Development` 或 `iOS Distribution`，然后点击 `Continue` 按钮。

![](https://res.wx.qq.com/op_res/N9atswqKJU7px-H_obE20S_p0PjHOKk4MNbJ4bDPJcOiVGBvPKf4wnJcoE4pRSeoq36Y3B0cemR68xdzxBDWyg)

4. 将 3.1 步生成的 `certSigningRequest` 文件，上传至页面中，然后点击 `Continue` 按钮。

![](https://res.wx.qq.com/op_res/N9atswqKJU7px-H_obE20bY9WGLt_FfNksCfOqXf1rWvSvhoPRQ-qGC6iu5aZn3OFRF1g6G29iXEgKDQytPQdQ)

5. 创建流程结束后，在页面中点击 `Download` 按钮下载证书。

![](https://res.wx.qq.com/op_res/N9atswqKJU7px-H_obE20XodwB05Mi8p8H0t1QizvxfrdiFqI3vmRPEPbdivNDjDm-gXmDsUlg-LJ50o2fJgmw)

### [#](#_3-3-导出-P12) 3.3 导出 `P12`

1. 将 3.2 步下载的 `development.cer` 文件下载到 `macOS` 电脑端，然后打开，会自动加载「钥匙串」。

![](https://res.wx.qq.com/op_res/HKTvTiYPfwfrnOo1sYEsaOLUBv_o4qGknUUnG4dmyslDeSm6NSdLnDAov5uCb2cd2JC3w1TR0fBsSJSUmd21XQ)

2. 如果查看时，显示证书「不可信任」，则需要在 `Certificates` 创建页底部，下载证书，一同安装。

![](https://res.wx.qq.com/op_res/N9atswqKJU7px-H_obE20UNOzk5mhECBQi-ILHkdniPMoCc7XTdX9sXkcY5slt1Zk0HkQYH3wcVP7pL6dR8sHQ)

3. 安装后，`development.cer` 证书会变为已信任状态，如下图所示。

![](https://res.wx.qq.com/op_res/HKTvTiYPfwfrnOo1sYEsaL3uZaP6BPJSAWEj-sWF1rSYSlumRmc4ipVQQMC7tGskmUaVmzVfzJsteUYi3jA4TQ)

4. 将「钥匙串」中导入的证书复制到「登录」中，在证书 TAB 中，选择导入的证书右键导出。

![](https://res.wx.qq.com/op_res/HKTvTiYPfwfrnOo1sYEsaDhJPAFpw5YqNDUpHTt0wAD9JTRJwoK_ekvyVqd4hP3jz6PTsfLJ4aZh8m4p9VNBUA)

导出类型选择 `p12`，按照对话框提示设置密码（要记住这个密码）

> 如果 p12 不可选择，需要注意 3.1 步操作电脑和导出 P12 的电脑一致，钥匙串中密钥有 3.1 步设置的密钥名，没有就无法关联密钥，也就无法导出 p12 文件。另外 3.1 步设置在「登录」区，所以证书从「系统」复制到「登录」再导出。

5. 导出 `p12` 文件后，需要妥善保存以及记住密码。（在后续各处环节都需要用到）

## [#](#四、创建-Provisioning-Profile) 四、创建 Provisioning Profile

### [#](#_4-1-创建-appID（bundleID）) 4.1 创建 appID（bundleID）

1. 使用 Apple 开发者账号登录 [Developer 控制台](https://developer.apple.com/account)，前往「证书、标识符和描述文件」进入「标识符」页面。

> 没有 Apple 开发者账号需要先注册并认证账号为可用，否则接下来的步骤完成不了。

![](https://res.wx.qq.com/op_res/GIW9qpUZ3UpNuH8YiCxmzhMpyTbR6jCDhzRxXw07i5RdSg9z0x4X_kxPAVfdJ3vX55DFZ0LvAs4uugcj99svCg)

2. 点击 `Identifiers` 后的「+」号，进入 `Register a new identifier` 环节

![](https://res.wx.qq.com/op_res/GIW9qpUZ3UpNuH8YiCxmzqP63sr6yQ6NeBA-q2nwUVnY5TKPnjdsuZL2f61rYO3eKK35Juxu-5GOXNCSUh4zbg)

3. 选择 `App IDs`，然后点击 `Continue` 按钮。

![](https://res.wx.qq.com/op_res/GIW9qpUZ3UpNuH8YiCxmzv9L4xGGl77NcnVSLaPVviKNVzHwsphDHVDXSxfqv6R6RUqFUaQJhvtlxMlEblLwmw)

4. 继续，`Select a type` 为 `App`，然后点击 `Continue` 按钮。

![](https://res.wx.qq.com/op_res/GIW9qpUZ3UpNuH8YiCxmzmO5BBgRP4lRNUhCY2qnOa1KfBannFcJZnURdeoZpOOwM5S3DI3_JWmzhtCXVLotjA)

5. 在 `Register an App ID` 页面，按下图所示完成填写。

![](https://res.wx.qq.com/op_res/GIW9qpUZ3UpNuH8YiCxmzsPVyJJnbzAWsV18hBcOhCcuSRH4E3c5IlyB9Qcou0ejcFpC74MqkxSt_BOancaPrQ)

**Description**：是你做标记的描述，可以任意填写。
**Bundle ID**：建议是 `Explicit`，输入框中为反写的自有域名，比如 `com.qq.xx`（写你自己的，不要写这个）

必要的权限如下：

- Access WiFi Information
- Associated Domains
- Hotspot
- Wireless Accessory Configuration

如果使用了多端身份管理模块，请再开启苹果登录权限：

- Sign In with Apple

如果使用的其他原生插件要求开启对应权限，如苹果支付，也配置开启对应权限。

6. 继续点击 `Continue` 按钮，就成功创建 `appID`，在第 5 步中填写的 **Bundle ID**，需要记录下来。多端框架绑定的「开放平台-移动应用」在申请 iOS 开发时，需要填写此 **Bundle ID**。

### [#](#_4-2-配置-Devices) 4.2 配置 Devices

1. 使用 Apple 开发者账号登录 [Developer 控制台](https://developer.apple.com/account)，前往「证书、标识符和描述文件」进入「设备」页面。

![](https://res.wx.qq.com/op_res/HKTvTiYPfwfrnOo1sYEsaH_R3bLhWBaYrf377bFL0jIvHzOhuvKqKZ47CIKnsmCFGuNCqcOgXKU53npo_UmsmA)

2. 点击 `Devices` 后的「+」号，进入 `Register a New Device` 环节

![](https://res.wx.qq.com/op_res/HKTvTiYPfwfrnOo1sYEsaDAPWU_AucEIqxU2oSXZbe9kn2VOvXW9GPSTWaiAeWBn9jEDzfRY7HdI6D4lQGY92g)

3. 填写设备 `Device ID`（`UDID`），并填写 `Device Name` 设备名，这里推荐使用 iPhone 设备来配置。
   ![](https://res.wx.qq.com/op_res/HKTvTiYPfwfrnOo1sYEsaGtrZqdwXKjZwIZi4kP9j-jjrv5UTpFk2SaTWz7zs2R-7ty_pQkVnAdA7iqWGdnhqQ)
4. 不知道 iPhone 设备的 `Device ID`（`UDID`），请使用 Xcode 获取。

![](https://res.wx.qq.com/op_res/lq7QWvtiWrNKz-beiTGmLQW2lztQ0TVXgq8YAdYPYztdBgSfZtnZIEYlsJ3m1lAt9uSnwJ050aLPKNOzEK6TCg)

5. 配置好后，根据账号情况可能立刻就能生效，也可能需要 24-72 小时确认，当不出现 `processing` 的 `Status` 字样时则该设备可用。

### [#](#_4-3-创建-Profiles) 4.3 创建 Profiles

1. 使用 Apple 开发者账号登录 [Developer 控制台](https://developer.apple.com/account)，前往「证书、标识符和描述文件」进入「描述文件」页面。

> 没有 Apple 开发者账号需要先注册并认证账号为可用，否则接下来的步骤完成不了。

![](https://res.wx.qq.com/op_res/lq7QWvtiWrNKz-beiTGmLee9LWvUmYHr6p9UwnYakMHeUeH0unM6pVXsl2e30D6iqxSQ65Tz2fdnKcbUMH7MUg)

2. 点击 `Profiles` 后的「+」号，进入 `Register a New Provisioning Profile` 环节

![](https://res.wx.qq.com/op_res/lq7QWvtiWrNKz-beiTGmLQpwRj7-PFHldU0c-nFGEbFeRt-hSdREnJYgOdW0IMb8rmBXkUUbCHUcprDp_Wc_vw)

3. 如果是开发选择 `iOS App Development`，上架审核选择 `App Store Connect`

![](https://res.wx.qq.com/op_res/lq7QWvtiWrNKz-beiTGmLaArEQuImGIBhgmd9xuR5PaRRJD7DNzLlWzMFn1SwrNVV_wJxjYYL35WwjWxjUvDiQ)

4. `Select an App ID` 中 App ID，选择 4.1 步创建的 `App ID`

![](https://res.wx.qq.com/op_res/lq7QWvtiWrNKz-beiTGmLQcDUNoTNZHZaMHjgPAnCX9fZ8IEPNt9LaDn8vruZTv0jlQq5CDkh1mwhAIfkiBc3w)

5. `Select Certificates` 选择 3.2 步创建的 `Certificates`

![](https://res.wx.qq.com/op_res/lq7QWvtiWrNKz-beiTGmLYKAPlZyMQqC_SGjlhNPqax96VcuSPppCPxsCvwJu2xPl8AVadk1Et_DQ2hlUYSibA)

6. `Select Devices` 选择在 4.2 步登记的 `Devices`

![](https://res.wx.qq.com/op_res/lq7QWvtiWrNKz-beiTGmLXQIkuDcbNvUeAUq3sv_qSAkT4b7PVLHGGqNtBiTgPXIpvlEcml_JmHfQjIVvkPZ5w)

7. `Review, Name and Generate` 环节，填写 `Profile Name`，点击 `Generate` 按钮
   ![](https://res.wx.qq.com/op_res/t2eAm2wq3H-fVbrYygNXV-9ggGMg-p0Q5j-fY5k7vV987K5i2WkHXStQjl4dGCWi9Bi15kHw_btSFo5gln9gMA)
8. 生成后，可以在列表中进入该 `Profile`，下载 `mobileprovision` 文件。

![](https://res.wx.qq.com/op_res/t2eAm2wq3H-fVbrYygNXV3VRJpFXZR5t6tcnkjXxZe8huNRgEoZ4Ise_2Ndmms9qMjumJYKAMegLR8prmly23A)

9. 我们需要保存此 `mobileprovision` 文件。

## [#](#五、iOS-真机运行和构建配置) 五、iOS 真机运行和构建配置

1. 在「微信开发者工具」中真机运行使用「证书签名」，或者在构建时选「证书签名」且「不使用分发证书」时，主要需要 `Certificate` 和 `Provisioning Profile` 两个文件，以及 `Certificate` 的证书密码。

![](https://res.wx.qq.com/op_res/nw0yXao5eKwmuJAr1D4qLKH0IBm8iAe5kTkiCmvviRsV0bObMZueB_RXZLIJE1FplwdpAGgPEpF3ZVdzIvdRpQ)

- **Certificates Path**：在 3.3 步骤中导出的 `p12` 文件。
- **Certificates Password**：在 3.3 步骤中导出 `p12` 文件时设置的密码。
- **Profile**：在 4.3 步骤中创建下载的 `mobileprovision` 文件。
- **签名证书名（如有）**：直接填写 3.3 步骤中证书 `Apple Development:` 后的内容。

2. 在构建时选「证书签名」且「使用分发证书」时，会需要设置 `Certificate`（P12 文件）和 `Provisioning Profile` 文件，以及 `Certificate`（P12 文件）的证书密码。

![](https://res.wx.qq.com/op_res/t2eAm2wq3H-fVbrYygNXV30yKTdclregy3SxCl-_AM9eqgMmfe4yrBFtFokA5N5Xl2lUuFnSFshKDLceDPQ0pQ)

- **P12证书**：在 3.3 步骤中导出的 `p12` 文件。
- **P12密码**：在 3.3 步骤中导出 `p12` 文件时设置的密码。
- **Profile**：在 4.3 步骤中创建下载的 `mobileprovision` 文件。
- **签名证书名**：直接填写 3.3 步骤中证书 `Apple Development:` 后的内容。

![](https://res.wx.qq.com/op_res/HKTvTiYPfwfrnOo1sYEsaL3uZaP6BPJSAWEj-sWF1rSYSlumRmc4ipVQQMC7tGskmUaVmzVfzJsteUYi3jA4TQ)

Incorrect translation.