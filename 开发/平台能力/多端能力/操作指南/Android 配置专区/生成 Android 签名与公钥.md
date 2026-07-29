# [#](#生成-Android-签名与公钥) 生成 Android 签名与公钥

开发者可使用此工具生成 Android 签名作为微信开放平台移动应用的 Android 的签名，以及可以生成公钥用于 App 备案。

说明：需使用最新的 nightly 开发者工具；即，如你的开发者工具无此功能，需将开发者工具升级到最新 [nightly](https://developers.weixin.qq.com/miniprogram/dev/devtools/log)。

## [#](#一、生成-Android-签名与公钥) 一、生成 Android 签名与公钥

前往微信开发者工具 - 工具栏 - 设备选择下拉栏 - 签名证书管理 - Android 签名与公钥。

![](https://res.wx.qq.com/op_res/4rrN_3d232K5xn35BPniwM2lustT_THoVIRZcYq2y5CPM1SKyAWyf3PYPesrc35JEJx9BcGIff2Nz1oCNeoR8w)

选中 APK 用于生成 Android 签名与公钥。

![](https://res.wx.qq.com/op_res/4rrN_3d232K5xn35BPniwHd3OMlk2cSUDvtcuWi4Vg-3bTcBTNWt6kerB_VwCY34gfmiebD_dnV2FoNzVUwyCA)

点击「生成」即可同时生成签名与公钥。

![](https://res.wx.qq.com/op_res/4rrN_3d232K5xn35BPniwDn7_mAqN-M88cLxBBNQOfsSQhZadWh57BjLN8wvh5iC7J2yGRrvB18-JD0vOeHIYQ)

## [#](#二、将-Android-签名填至微信开放平台「移动应用」配置处) 二、将 Android 签名填至微信开放平台「移动应用」配置处

将生成的 Android 签名填入「移动应用」配置处。

- 若此 APK 使用了微信开放能力（例如微信分享、微信登录、微信支付等），那么此多端应用所绑定的移动应用所配置的签名需与步骤 1 中生成的签名一致，否则会出现如下报错：

  ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202311021601024.png)

- 解决方案：可将 Android 签名填至微信开放平台移动应用，确保两边的配置是一致的。

  ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202311021604888.png)

**注意**

- 使用的证书不一样会导致生成的签名不一样；开发者需保存好签名证书信息，请勿丢失。

## [#](#三、将-Android-签名与公钥填至-App-备案平台) 三、将 Android 签名与公钥填至 App 备案平台

按照[《工业和信息化部关于开展移动互联网应用程序备案工作的通知》](https://www.miit.gov.cn/zwgk/zcwj/wjfb/tz/art/2023/art_920db564162e4312916a01bed6540ad8.html)，2023 年 9 月 1 日起，需履行备案手续后才能上架应用市场。而进行 Android App 备案的过程中需将「App 特征信息」填写至备案平台，其中涉及「平台公钥以及签名 MD5 值」便是按照步骤 1 生成的 Android 签名与公钥。

- 以腾讯云的 [APP 备案所需的 APP 特征信息填写参考规范](https://cloud.tencent.com/document/product/243/97789#b4df5546-b1ab-46cf-9ef0-c984a546a477)为例，该指引提供了详细的步骤描述关于如何获取「iOS 系统获取 Bundle ID、平台公钥、签名 MD5 值」以及如何获取「Android 系统获取包名、平台公钥、签名 MD5 值」。
- 文中是以通过「jadx-gui」工具获取相关信息为例，而对于使用多端框架构建的 APK，则可按照步骤 1 中使用微信开发者工具即可快速生成签名与公钥。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202311021822618.png)

## [#](#补充：iOS-备案) 补充：iOS 备案

以腾讯云的 [APP 备案所需的 APP 特征信息填写参考规范](https://cloud.tencent.com/document/product/243/97789#b4df5546-b1ab-46cf-9ef0-c984a546a477)为例，该指引提供了详细的步骤描述关于如何获取「iOS 系统获取 Bundle ID、平台公钥、签名 MD5 值」，iOS App 备案可参考上面的文档

此外，关于更多 App 备案相关指南可查看：

- [APP 备案相关 FAQ](https://cloud.tencent.com/document/product/243/97691)
- [一图读懂 APP 备案](https://www.miit.gov.cn/jgsj/xgj/hlwgl/art/2023/art_fd468b6fe66b4c05b8e3546566fd8265.html)
- [APP 备案服务内容目录](https://cloud.tencent.com/document/product/243/100155)
- 审核通过后可通过[备案管理系统](https://beian.miit.gov.cn/)查看备案结果
- 更多的指南可前往[腾讯云](https://cloud.tencent.com/document/product/243/97668)进行查看

Incorrect translation.