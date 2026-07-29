# [#](#Android-签名证书管理) Android 签名证书管理

Android 签名证书的应用场景有如下：

- 在微信开发者工具运行于 Android 模拟器和真机前需配置证书项目信息
- 在微信开发者工具构建 APK 时需配置证书项目信息

使用上述功能时，首先会出现 Android 签名证书管理，后续如需对签名进行修改可在「工具栏 - 选择设备 - 签名证书管理 - Android 签名证书管理」进行管理。

![](https://res.wx.qq.com/op_res/zIKD3ISB-difV0lWmPcj3G-RRf1U5LDzeQTUbm0t8eastaD4-Bkvb9qCMFxa88HKjY-dzDVS0iex6PUDRVHJ-A) ![](https://res.wx.qq.com/op_res/zIKD3ISB-difV0lWmPcj3FV6UZlDfoEShQyLpUtV5l7wvvhFd6g5tKICAsE9UKCCUZdaP_Ry71SN2AbjBbSaiw)

相关的说明如下：

- 证书别名：即证书的 key-Alias，该配置项为必填
- 证书密码：即证书的 key-Password，该配置项为必填
- 证书文件密码：即证书的 storePassword，该配置项为必填

补充：关于如何生成 `keystore` 证书可查看[生成 Android 证书与签名](android-cert)。

Incorrect translation.