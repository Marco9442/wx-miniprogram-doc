# [#](#通过-CI-打包-miniprogram-ci) 通过 CI 打包(miniprogram-ci)

开发者可通过 miniprogram-ci 构建 APK 和 IPA，开发者需要先学习[miniprogram-ci](https://www.npmjs.com/package/miniprogram-ci) 使用。

## [#](#_1、安装) 1、安装

`npm install miniprogram-ci@alpha`

## [#](#_2、构建-APK) 2、构建 APK

### [#](#示例代码) 示例代码

```
const ci = require('miniprogram-ci')
;(async () => {
  const project = new ci.Project({
    appid: 'wxsomeappid',
    type: 'miniProgram',
    projectPath: 'the/project/path',
    privateKeyPath: 'the/path/to/privatekey',
    ignores: ['node_modules/**/*'],
  })
  const buildResult = await ci.buildApk({
    project,
    keyAlias: 'keyAlias',
    keyPass: 'keyPass',
    keyStore: 'the/path/to/keystore',
    storePass: 'storePass',
    output: '/the/path/to/output',
    desc: 'build apk from ci',
  })
  console.log(uploadResult)
})()
```

### [#](#参数) 参数

#### [#](#请求参数) 请求参数

- 同时支持传入 ci.uploaod 的参数

| 键 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| project | IProject | 是 | #项目对象 |
| keyStore | string | 是 | 证书文件绝对路径 |
| keyPass | string | 是 | 证书密码 |
| storePass | string | 是 | 证书文件密码 |
| keyAlias | string | 是 | 证书别名 |
| output | string | 是 | 构建产物的保存路径，需要为系统绝对路径 |
| useAab | boolean | 否 | 默认 false |
| desc | string | 否 | 版本描述 |
| isUploadResourceBundle | boolean | 否 | 是否上传资源包 |
| resourceBundleVersion | string | 否 | 资源包版本号 |
| resourceBundleDesc | string | 否 | 资源包项目备注 |
| disableCache | boolean | 否 | 是否清除构建缓存 |

#### [#](#返回参数) 返回参数

| 键 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errmsg | string |  | 构建信息 |
| success | boolean |  | 构建是否成功 |

## [#](#_3、构建-IPA) 3、构建 IPA

支持本地构建与远程构建。本地构建 IPA 仅支持在 macOS 上使用 codesign 进行签名，因此开发者需要确保 keychains 中包含自己的证书信息。Windows 可以使用远程构建。

### [#](#示例代码-2) 示例代码

```
const ci = require('miniprogram-ci')
;(async () => {
  const project = new ci.Project({
    appid: 'wxsomeappid',
    type: 'miniProgram',
    projectPath: 'the/project/path',
    privateKeyPath: 'the/path/to/privatekey',
    ignores: ['node_modules/**/*'],
  })
  const buildResult = await ci.buildIpa({
    project,
    output: '/the/path/to/output', // 构建产物的保存路径，需要为系统绝对路径
    profilePath: '/the/path/to/profile', // profile 文件地址，文件格式为 mobileprovision，相对项目根路径的相对路径
    certificateName: 'Apple Develop', // 签名证书名
    tpnsProfilePath: '/the/path/to/tnpsprofile', // tpnsProfile 文件路径，相对项目根路径的相对路径
  })
  console.log(uploadResult)
})()
```

### [#](#参数-2) 参数

#### [#](#参数-3) 参数

同时支持传入 ci.uploaod 的参数。

| 键 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| project | IProject | 是 | #项目对象 |
| output | string | 是 | 构建产物的保存路径，需要为系统绝对路径 |
| isDistribute | string | 否 | 是否使用分发证书 |
| profilePath | string | 是 | profile 文件地址，文件格式为 mobileprovision，相对项目根路径的相对路径 |
| certificateName | string | 是 | 证书别名 |
| tpnsProfilePath | string | 否 | tpnsProfile 文件路径，相对项目根路径的相对路径 |
| p12Path | string | 否 | p12 文件路径，文件格式为 p12，相对项目根路径的相对路径。使用远程构建时必填 |
| p12Password | string | 否 | p12 密码。使用远程构建时必填 |
| desc | string | 否 | 版本描述 |
| isUploadResourceBundle | boolean | 否 | 是否上传资源包 |
| resourceBundleVersion | string | 否 | 资源包版本号 |
| resourceBundleDesc | string | 否 | 资源包项目备注 |
| disableCache | boolean | 否 | 是否清除构建缓存 |
| isRemoteBuild | boolean | 否 | 是否使用远程构建 |

#### [#](#返回) 返回

| 键 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errmsg | string |  | 构建信息 |
| success | boolean |  | 构建是否成功 |

## [#](#_4、上传资源包) 4、上传资源包

### [#](#示例代码-3) 示例代码

```
const ci = require('miniprogram-ci')
;(async () => {
  const project = new ci.Project({
    appid: 'wxsomeappid',
    type: 'miniProgram',
    projectPath: 'the/project/path',
    privateKeyPath: 'the/path/to/privatekey',
    ignores: ['node_modules/**/*'],
  })
  const uploadResult = await ci.miniappCloudUpload({
    project,
    version: '0.1.24',
    androidPlatform: false,
    setting: {
      es6: true,
    },
  })
  console.log(uploadResult)
})()
```

### [#](#参数-4) 参数

#### [#](#参数-5) 参数

同时支持传入 ci.uploaod 的参数。

| 键 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| project | IProject | 是 | #项目对象 |
| version | string | 是 | 版本号 |
| desc | string | 否 | 版本描述 |
| iOSPlatform | boolean | 否 | 适用平台 iOS，默认为 true |
| androidPlatform | boolean | 否 | 适用平台 Android，默认为 true |

#### [#](#返回-2) 返回

| 键 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errmsg | string |  | 构建信息 |
| success | boolean |  | 构建是否成功 |

Incorrect translation.