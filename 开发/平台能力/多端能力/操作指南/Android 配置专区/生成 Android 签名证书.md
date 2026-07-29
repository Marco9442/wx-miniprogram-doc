# [#](#生成-Android-签名证书) 生成 Android 签名证书

> Android APK 调用其他如微信 Open SDK，通常需要对应用进行签名，从而绑定签名后的 md5 值。
> 可理解为： sign（你的 App）= 固定的应用签名（md5）

## [#](#一、生成签名证书) 一、生成签名证书

首先，应用签名需要先生成一个「签名证书」，如已有签名证书可跳过这步阅读。

签名证书常规有两种格式 `jks` 和 `keystore`，前者可以通过 `Android Studio` 生成，后者可通过 `keytool` 命令生成。

- 不同应用市场的签名证书的格式要求存在差异，用户选择性生成所需的证书，然后两个证书也是可以互相转换的。
- 在微信开放平台创建移动应用需配置的签名为通过 `keystore` 生成的，因此本文仅介绍生成 keystore 证书的方法。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202307102321305.png)

### [#](#_1-1-生成-keystore-证书) 1.1 生成 keystore 证书

#### [#](#方式-1：使用-keystore-命令工具生成证书) 方式 1：使用 keystore 命令工具生成证书

使用 keytool -genkey 命令生成证书：

```
keytool -genkey -alias testalias -keyalg RSA -keysize 2048 -validity 36500 -keystore test.keystore
```

- `testalias` 是证书别名，可修改为自己想设置的字符，建议使用英文字母和数字。
- `test.keystore` 是证书文件名称，可修改为自己想设置的文件名称，也可以指定完整文件路径。
- `36500` 是证书的有效期，表示 100 年有效期，单位天，建议时间设置长一点，避免证书过期。

补充说明：需先安装 JDK

回车后会提示：

```
Enter keystore password:  //输入证书文件密码，输入完成回车  
Re-enter new password:   //再次输入证书文件密码，输入完成回车  
What is your first and last name?  
  [Unknown]:  //输入名字和姓氏，输入完成回车  
What is the name of your organizational unit?  
  [Unknown]:  //输入组织单位名称，输入完成回车  
What is the name of your organization?  
  [Unknown]:  //输入组织名称，输入完成回车  
What is the name of your City or Locality?  
  [Unknown]:  //输入城市或区域名称，输入完成回车  
What is the name of your State or Province?  
  [Unknown]:  //输入省/市/自治区名称，输入完成回车  
What is the two-letter country code for this unit?  
  [Unknown]:  //输入国家/地区代号（两个字母），中国为CN，输入完成回车  
Is CN=XX, OU=XX, O=XX, L=XX, ST=XX, C=XX correct?  
  [no]:  //确认上面输入的内容是否正确，输入y，回车  
Enter key password for <testalias>  
        (RETURN if same as keystore password):  //确认证书密码与证书文件密码一样（HBuilder|HBuilderX要求这两个密码一致），直接回车就可以
```

以上命令运行完成后就会生成证书。

#### [#](#方式-2：使用开发者工具的「Android-签名证书生成」工具) 方式 2：使用开发者工具的「Android 签名证书生成」工具

操作路径为：工具栏 - 选择设备 - 签名证书管理 - Android 签名证书生成。

![](https://res.wx.qq.com/op_res/3JabgPDvh4sx5bpgvY4oqZNLmsSqbM3xokXql4qD_3XQo0huRq0NYtFQ9dDQIXtB99O7-B8gf1lBiIvlyDkhow)

按照要求填入下方信息即可生成证书。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202307182304789.png)

补充说明：

- 证书别名：即证书的 key-Alias，该配置项为必填
- 证书密码：即证书的 key-Password，该配置项为必填
- 证书文件密码：即证书的 storePassword，该配置项为必填
- 成功后，即可前往证书文件路径中查看已生成的证书文件

![](https://res.wx.qq.com/op_res/3JabgPDvh4sx5bpgvY4oqXUq9SotzvJ1R5gDUtr3TCXaU3amCim8Gpfv5CBD2tfZMJUvRV__eYIMC25tJ0P77w)

## [#](#二、签名证书使用) 二、签名证书使用

生成的签名证书有如下应用场景：

- 在微信开发者工具运行于 Android 模拟器和真机前需配置证书项目信息
- 在微信开发者工具构建 APK 时需配置证书项目信息
- 用于生成签名填写于微信开放平台移动应用的开发信息中

### [#](#_2-1-运行于模拟器和真机) 2.1 运行于模拟器和真机

首次运行于 Android 模拟器和真机时会出现如下签名管理弹窗：

![](https://res.wx.qq.com/op_res/3JabgPDvh4sx5bpgvY4oqfNsPQaG31tJ_2NOltzXTwZrOujP54-73PSYxAjpANHxTkE78fC4ZMr0NOjbuIN_Ng)

相关的说明如下：

- 证书别名：即证书的 key-Alias，该配置项为必填
- 证书密码：即证书的 key-Password，该配置项为必填
- 证书文件密码：即证书的 storePassword，该配置项为必填

### [#](#_2-2-构建-APK) 2.2 构建 APK

构建 APK 时需要单独设置对应的签名证书信息，详情可查看[打包生成 APK](build-apk)。

- 即，通过上述方式配置的证书信息不会同步到「构建 APK」面板中，需重新配置用于构建正式 APK 的证书配置（但是推荐使用同一份，因为证书信息不一致会影响生成的签名的不一致，从而可能会在真机调试的时候没有签名，但是构建 APK 后出现「由于应用包签名信息校验不通过，无法分享到微信」的报错）。

### [#](#_2-3-生成应用签名和公钥) 2.3 生成应用签名和公钥

详情可查看[生成 Android 签名与公钥](record)。

Incorrect translation.