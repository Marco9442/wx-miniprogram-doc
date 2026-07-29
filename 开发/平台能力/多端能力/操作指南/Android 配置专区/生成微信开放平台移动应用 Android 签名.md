# [#](#生成微信开放平台移动应用-Android-签名) 生成微信开放平台移动应用 Android 签名

如果你的移动应用是使用平台推出的多端框架开发的，可查看本文的指引生成「应用签名」并填入下方配置中；如果你的移动应用并未使用平台的多端框架开发，需开发者自行生成「应用签名」并填入下方配置中。

![](https://res.wx.qq.com/op_res/wRJkKuPXbSc4Hu_nZ-fWvh6Gh6Vq1xJCSWuT96LLYEiN0qgyLsm0vqoht84B9zNymCIbWimx1qMChofhFcj4hw)

- 注意：如果 APK 不是使用小程序多端框架在微信开发者工具打包的，可参考这里通过[签名生成工具](https://developers.weixin.qq.com/doc/oplatform/Mobile_App/Downloads/Android_Resource)生成签名。

## [#](#一、使用流程介绍) 一、使用流程介绍

**当你的多端应用尚未绑定移动应用，可按照下方步骤操作：**

1. 在微信开发者工具构建 APK （需填写证书配置）
2. 在微信开发者工具生成 Android 签名
3. 在微信开放平台创建移动应用，创建过程中将步骤 2 生成的 Android 签名填入
4. 在微信开放平台提交移动应用审核，审核通过后，前往多端应用控制台将移动应用绑定到多端应用即可

**当你的多端应用已绑定移动应用，可按照下方步骤操作：**

1. 找出用于生成「在微信开放平台创建移动应用的时候填的 Android 签名」所需的证书信息（包含证书别名、密码、证书文件等）
2. 在微信开发者工具构建 APK （必须使用步骤 1 中的证书配置，否则最后生成的签名和微信开放平台填写的不一致）
3. 在微信开发者工具生成 Android 签名，用于验证是否和微信开放平台填写的一致，如果不一致，那么则是证书信息不对导致的

**补充**

- 如果忘记了生成「在微信开放平台创建移动应用的时候填的 Android 签名」所需的证书信息，那么建议你使用新的证书信息重新构建 APK，重新生成签名，然后修改微信开放平台移动应用的签名信息，然后重新提交审核等待审核通过即可。

## [#](#二、操作指引) 二、操作指引

### [#](#_2-1-构建-APK) 2.1 构建 APK

在微信开发者工具中，点击「构建 - 打包生成 APK」，按照[文档](android-cert)生成证书，填写其他信息，然后构建。

- 关于证书配置里的内容如何填写，可查看文档[生成 Android 证书](android-cert)。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202308121800711.png)

### [#](#_2-2-生成应用签名) 2.2 生成应用签名

前往微信开发者工具 - 工具栏 - 设备选择下拉栏 - 签名证书管理 - Android 签名与公钥。

![](https://res.wx.qq.com/op_res/4rrN_3d232K5xn35BPniwM2lustT_THoVIRZcYq2y5CPM1SKyAWyf3PYPesrc35JEJx9BcGIff2Nz1oCNeoR8w)

选中 APK 文件用于生成 Android 签名与公钥。

![](https://res.wx.qq.com/op_res/4rrN_3d232K5xn35BPniwHd3OMlk2cSUDvtcuWi4Vg-3bTcBTNWt6kerB_VwCY34gfmiebD_dnV2FoNzVUwyCA)

点击「生成」即可同时生成签名与公钥。

![](https://res.wx.qq.com/op_res/4rrN_3d232K5xn35BPniwDn7_mAqN-M88cLxBBNQOfsSQhZadWh57BjLN8wvh5iC7J2yGRrvB18-JD0vOeHIYQ)

### [#](#_2-3-将-Android-签名填至微信开放平台「移动应用」配置处) 2.3 将 Android 签名填至微信开放平台「移动应用」配置处

若此 APK 使用了微信开放能力（例如微信分享、微信登录、微信支付等），那么此多端应用所绑定的移动应用所配置的签名需与步骤 1 中生成的签名一致，否则会出现如下报错：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202311021601024.png)

**补充**

- 如果「真机运行」的时候没有出现「由于应用包签名信息校验不通过，无法分享到微信」的报错，但是构建 APK 装到手机后却出现了此问题，则是因为运行于真机的时候配置的证书信息和构建 APK 的时候填写的证书信息不一致导致的。
- 因为，使用的证书不一样会导致生成的签名不一样。
- 因此，开发者需保存好签名证书信息，请勿丢失。

**解决方案**

- 可将 Android 签名填至微信开放平台移动应用，确保两边的配置是一致的。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202311021604888.png)

### [#](#_2-4-提交审核并等待审核通过) 2.4 提交审核并等待审核通过

审核通过后，即可将该移动应用绑定到多端应用中，绑定后，在微信开发者工具中「构建 - 打包生成 APK」面板中，即会显示开发者自定义的 Package Name。

![](https://res.wx.qq.com/op_res/7ydWCU4N969GCTonD-y95Qr_AgPSWoYKfgOb2NfvxtFEj9m79HIzbrHTRDIunnRcV-pcBM6hUi_B9qGlmEHzOA)

### [#](#_2-5-（可选）重新生成应用签名) 2.5 （可选）重新生成应用签名

如证书遗失或者其他原因导致需更新证书，重新生成签名，则可前往微信开放平台移动应用进行修改，修改后重新提审，待审核通过后多端应用则会以最新的包名和签名生成安装包。

Incorrect translation.