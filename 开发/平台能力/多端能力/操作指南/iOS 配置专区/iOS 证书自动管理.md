# [#](#iOS-证书自动管理) iOS 证书自动管理

为方便开发者更高效地生成 iOS 证书签名所需的 p12 文件以及 profile 文件，开发者工具 (`版本号 >= 1.06.2412042`) 新增支持「iOS 证书自动管理」功能。

## [#](#一、能力概览) 一、能力概览

开发者需在项目的 `project.miniapp.json` 文件配置 `Apple Connect` 信息，即可开启该能力。

![](https://res.wx.qq.com/op_res/mXZVhCufWXWbkbg9WnzYfFc0Nb82y36dqYt-4wJEMadFMerO26UWcsIAMNDf7nDu2DIZXJkH9MrwTuv5wv8mMg)
> 配置信息的获取请看第二部分

开启后在以下位置时，可以使用自动管理：

### [#](#_1-1-工具栏-选择设备-签名证书管理) 1.1 工具栏 - 选择设备 - 签名证书管理

![](https://res.wx.qq.com/op_res/mXZVhCufWXWbkbg9WnzYfD3frEZjzlDw3uqV3WwvM0dlRm--biT-YqRKdyGJwpAe_1Up3_oUU6Txm3eP90Y6Aw) ![](https://res.wx.qq.com/op_res/mXZVhCufWXWbkbg9WnzYfOSeSdju2wS6SwcsU2mmHhYkM2HMA_ftWMeLxai5Iz5_qQPOh9PuBlWfYte6tmLwgQ)

### [#](#_1-2-工具栏-构建-打包生成-IPA-证书配置) 1.2 工具栏 - 构建 - 打包生成 IPA - 证书配置

![](https://res.wx.qq.com/op_res/mXZVhCufWXWbkbg9WnzYfJoLTqcxvSNnbPEGgmaDtlm2lFvP4O1hZOrKCGhsG0ylmQqVWZTB3MRoW5Y1ISA0Tw) ![](https://res.wx.qq.com/op_res/mXZVhCufWXWbkbg9WnzYfMlTNnbUojupYKvuYFwVXW4hkvkcRcQU2MKIX7R08cYDZq0YWFhprTh-uHb-Cvn_Vw)

## [#](#二、Apple-Connect-配置获取与配置) 二、Apple Connect 配置获取与配置

> 关于 `Apple Connect` 详细的介绍以及完整的操作说明可前往 [Apple 官方文档](https://developer.apple.com/documentation/appstoreconnectapi/creating-api-keys-for-app-store-connect-api) 查看，本文仅以「团队」密钥为例子提供部分操作说明。
>
> 说明：API 密钥有两种类型，分别是团队和个人。

### [#](#_2-1-登录-appstoreconnect-并进入「用户和访问」) 2.1 登录 `appstoreconnect` 并进入「用户和访问」

前往[https://appstoreconnect.apple.com](https://appstoreconnect.apple.com/login)并登录。然后点击「用户和访问」。

![](https://res.wx.qq.com/op_res/mXZVhCufWXWbkbg9WnzYfE2ftTT3TTNGt6mANuBP1745kcuF15vcTHrN7a_sB_psc88DrVfOuJp5TOg4ndQEtg)

### [#](#_2-2-编辑或查看密钥信息并下载-p8-文件) 2.2 编辑或查看密钥信息并下载 p8 文件

选择「团队密钥」，并复制 `issuer id` 和密钥 `id`（该信息需填至开发者工具 project.miniapp.json 文件中）

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202412042010927.png)
> 注意：生成密钥时开发者需要注意权限控制

![](https://res.wx.qq.com/op_res/mXZVhCufWXWbkbg9WnzYfGKyEgtzJzE_rI16sleZ__BRenaf2jjFTRL31ap0BvIUYXxQ8ZqOoRynmbWLQoDT3A)
> 注意：p8 文件只能下载一次；该信息需填至开发者工具 project.miniapp.json 文件中

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202412042014124.png) ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202412042015191.png)

### [#](#_2-3-在开发者工具配置-Apple-Connect-信息) 2.3 在开发者工具配置 Apple Connect 信息

![](https://res.wx.qq.com/op_res/mXZVhCufWXWbkbg9WnzYfFc0Nb82y36dqYt-4wJEMadFMerO26UWcsIAMNDf7nDu2DIZXJkH9MrwTuv5wv8mMg)
> 说明：在 1.2 中下载的 p8 文件需放置在当前项目目录中

## [#](#三、使用操作) 三、使用操作

### [#](#_3-1-运行) 3.1 运行

#### [#](#_3-1-1-未选中任何设备或者选中模拟器均无需配置签名信息) 3.1.1 未选中任何设备或者选中模拟器均无需配置签名信息

![](https://res.wx.qq.com/op_res/mXZVhCufWXWbkbg9WnzYfGBkQjdLgIhPge4kCTrqJlZS32LAqr5bJ9rp-3Mif2lF945F8olNJ_3qceha-VdrMA) ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202412042013148.png)

- 注意：p8 文件只能下载一次；该信息需填至开发者工具 project.miniapp.json 文件中

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202412042014124.png) ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202412042015191.png)

### [#](#_3-2-在开发者工具配置-Apple-Connect-信息) 3.2 在开发者工具配置 Apple Connect 信息

- 说明：在 1.2 中下载的 p8 文件需放置在当前项目目录中

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202412042016403.png)

## [#](#四、开发者工具操作指南) 四、开发者工具操作指南

### [#](#_4-1-运行) 4.1 运行

#### [#](#_4-1-1-未选中任何设备或者选中模拟器均无需配置签名信息) 4.1.1 未选中任何设备或者选中模拟器均无需配置签名信息

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202412041934294.png)

#### [#](#_4-1-2-选中真机即可按需配置签名信息) 4.1.2 选中真机即可按需配置签名信息

- **临时签名：** 使用 Apple ID 和密码即可
- **证书签名：** 需苹果开发者账号

![](https://res.wx.qq.com/op_res/mXZVhCufWXWbkbg9WnzYfOSeSdju2wS6SwcsU2mmHhYkM2HMA_ftWMeLxai5Iz5_qQPOh9PuBlWfYte6tmLwgQ)

#### [#](#_4-1-3-启用证书自动管理功能) 4.1.3 启用证书自动管理功能

完成 `Apple Connect` 信息配置后即可自动生成 `p12` 文件以及 `profile` 文件

![](https://res.wx.qq.com/op_res/mXZVhCufWXWbkbg9WnzYfOSeSdju2wS6SwcsU2mmHhYkM2HMA_ftWMeLxai5Iz5_qQPOh9PuBlWfYte6tmLwgQ)

若未完成 Apple Connect 信息配置，将无法启动证书自动管理功能

![](https://res.wx.qq.com/op_res/6smA79RYqlqYYGuO39CoOta5JSyVwBB69-rc8swnAAeGCNih3d16sNETwYI0Virv0tDsjftpBOQB0Ka4glwAtg)

##### [#](#_4-1-4-不启动「证书自动管理」功能，开发者仍可手动管理) 4.1.4 不启动「证书自动管理」功能，开发者仍可手动管理

选择已有的 p12 文件或者新创建 p12 文件

![](https://res.wx.qq.com/op_res/6smA79RYqlqYYGuO39CoOrudSUARUPPD40FUX8FiplV0Zlrbks2Vl9N9vU-apUZ0NRsMrMhqqhG-U2uGc5Y8mg)

选择对应的 profile 文件或新创建 profile 文件

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202412041956159.png)

完成相关配置后，点击确定即可构建并自动安装至真机并运行

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202412041957340.png)

### [#](#_4-2-构建) 4.2 构建

逻辑与 2.1 相同，均是：

需开发者前往 `project.miniapp.json` 配置 Apple Connect 信息方可正常使用该功能

完成 Apple Connect 信息配置后即选择启动「自动管理功能」，然后即可自动生成 p12 文件以及 profile 文件

开发者亦可不启动「证书自动管理」功能，继续使用原来的方式构建

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202412042000461.png)

## [#](#五、常见问题) 五、常见问题

### [#](#_5-1-报错提示：required-by-WeAppIdaas) 5.1 报错提示：required by WeAppIdaas

- 证书管理勾选「自动管理」后出现错误提示：get valid profile fail, bundleid capabilities not meet requirements. please tum on APPLE\_ID\_AUTH (required by WeApp|daas) in apple developer website（如下图）
- 出现此错误提示时，开发者需先确认 App 中是否需要用到 Apple 登录功能，如果需要，则需前往 [Apple 开发者平台](https://developer.apple.com/account) 开启 Apple 登录的权限；
- 如果确认 App 中无需使用到 Apple 登录功能，则开发者需前往开发者工具的 project.miniapp.json 中将「idaas SDK」取消勾选即可

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2Fwecom-temp-20368-630cff3f8e46409ed1bb2a848a3b9387.png)

### [#](#_5-2-报错提示：A-required-agreement-is-missing-or-has-expired) 5.2 报错提示：A required agreement is missing or has expired.

- 证书管理勾选「自动管理」后出现错误提示：request data got error return: A required agreement is missing or has expired. - This request requires an in-effect agreement that has not been signed or has expired.（如下图）
- 解决方案：前往 [Apple 开发者平台](https://developer.apple.com/account) 同意《Apple Developer Program License Agreement》或者《Apple Developer Agreement》即可

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202504011023780.png)

Incorrect translation.