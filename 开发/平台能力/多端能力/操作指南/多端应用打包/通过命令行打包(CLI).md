# [#](#通过命令行打包-CLI) 通过命令行打包(CLI)

- 若需在不依赖开发者工具场景如自身业务工程流水线上构建 APK 和 IPA，则推荐使用 <miniprogram-ci>。
- 在命令行构建的方式构建 APK 和 IPA 前，开发者需要先按照[开发者工具的命令行文档](https://developers.weixin.qq.com/miniprogram/dev/devtools/cli)准备执行命令的环境，以及查看基础的用法。

**步骤概览**

1. 根据文档执行 `cli open --project` 打开对应的项目
2. 使用`cli login` 登录
3. 成功进入项目后，执行 `cli build-apk` 或者 `cli build-ipa` 进行打包

## [#](#build-ipa) build-ipa

`cli build-ipa` 支持的参数如下：

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

## [#](#build-apk) build-apk

`cli build-apk` 支持的参数如下：

| 参数名 | 功能说明 | 是否必填 | 参数类型 |
| --- | --- | --- | --- |
| project | 项目路径，需要为系统绝对路径 | 是 | string |
| keyPass | 证书密码 | 是 | string |
| storePass | 证书文件密码 | 是 | string |
| keyAlias | 证书别名 | 是 | boolean |
| useAab | 是否发布为 AAB | 发布格式为 AAB 需要为 true（否则为 APK） | boolean |
| keyStore | 证书文件绝对路径 | 是 | string |
| desc | 版本描述 | 否 | string |
| output | 构建产物的保存路径，需要为系统绝对路径 | 是 | string |
| isUploadResourceBundle | 是否上传资源包 | 否，默认不上传 | boolean |
| resourceBundleVersion | 资源包版本号 | 否，如果选择上传资源包就必填 | string |
| resourceBundleDesc | 资源包项目备注 | 否，如果选择上传资源包就必填 | string |

示例：

```
/Applications/wechatwebdevtools.app/Contents/MacOS/cli build-apk --project /Users/zhangchen/WeChatProjects/miniprogram-18 --keyPass 123456 --storePass 123456 --keyAlias 123456 --useAab true --keyStore /Users/zhangchen/WeChatProjects/miniprogram-18/miniapp/android/android.keystore --output "/Users/zhangchen/Desktop/
```

Incorrect translation.