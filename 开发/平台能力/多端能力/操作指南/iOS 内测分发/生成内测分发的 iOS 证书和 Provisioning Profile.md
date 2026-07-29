# [#](#生成内测分发的-iOS-证书和-Provisioning-Profile) 生成内测分发的 iOS 证书和 Provisioning Profile

构建 IPA 时需选择 `.p12 文件`以及 `.mobileprovision` 文件，整体上和[生成 iOS 证书和 Provisioning Profile](../certificate/ios)步骤一致，不同点在于用于内测分发服务的证书需选择 `Development`，详细步骤如下：

- 补充：本文将直接从创建证书的步骤开始，创建 CSR 文件（证书请求文件）和创建 appID 的步骤本文不再赘述，开发者可前往[生成 iOS 证书和 Provisioning Profile](../certificate/ios)查看

## [#](#_1、创建证书) 1、创建证书

- 登录[苹果开发者平台](https://developer.apple.com/account/resources/certificates/list)，选择 Certificates，点击创建证书

![image](https://res.wx.qq.com/op_res/yX21ZZol4LPpF6CIso84k-RhsP25BLg9ZGy5YHYHkPUHjNyEEi0Z30UgRL2ojbkqehIvYa0rOQPQW-nVIxvVdQ
)

- 选择 software 类型。在内测分发的场景中，开发者需选择「Development」不可选「Distribution」

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312181250017.png)

- 选择 CSR 文件

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162109314.png)

- 然后下载 .cer 文件

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162110144.png)

- 双击 .cer 文件即可在「钥匙串访问」中查看

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162112712.png)

- 然后，可以选择对应证书，右键导出 p12 文件（包含私钥），这个用来对 iOS App 进行签名。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162115120.png)

## [#](#_2、创建配置文件（Provisioning-Profiles）) 2、创建配置文件（Provisioning Profiles）

- 登录[苹果开发者平台](https://developer.apple.com/account/resources/profiles/list)，点击创建 Profiles

![image](https://res.wx.qq.com/op_res/yX21ZZol4LPpF6CIso84k-IQwp-sQQiaRhdkNOivQVMnYU0TZ2J65OE9eX_3CR-cJ3c7AyqWD82LWSem-VHAIQ
)

- 选择类型

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312181251565.png)

- 选择与当前多端应用所配置的 Bundle ID 一致的 AppID

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162122352.png)

- 选择步骤 1 创建的证书

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162125656.png)

- 选择设备（可按需选择）

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162127525.png)

- 填写 Profile 名称

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162127558.png)

- 完成配置后，即可下载生成的 Profile 文件到本地

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162128418.png)

## [#](#_3、构建-IPA) 3、构建 IPA

- 在上述步骤中生成的 .p12 签名证书和 Profile 文件，并且选择对应的签名方式重新构建即可

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162130381.png)

- 选择 .p12 文件

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162130429.png)

- 选择 .mobileprovision 文件

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162133286.png)

- 构建完成

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162140279.png)

- 前往多端控制台 - 多端详情 - 内测分发，即可看到刚上传的内测版 IPA

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202312162141207.png)

Incorrect translation.