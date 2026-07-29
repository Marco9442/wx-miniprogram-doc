# [#](#构建鸿蒙应用操作指引) 构建鸿蒙应用操作指引

开发者工具 nightly 2.01.2509162 起正式支持构建鸿蒙应用，下方是使用说明。

## [#](#一、开发前须知) 一、开发前须知

鸿蒙应用相关能力逐步在完善中，如果遇到目前尚未对齐 Android 或 iOS 已有能力的需求，可前往[社区](https://developers.weixin.qq.com/community/develop/mixflow)反馈，评估后我们将尽快推进实现。

目前仍有一部分的组件和 JSAPI 尚未在鸿蒙端支持，可按照下方说明去索引并查看对应的组件和 JSAPI 是否已在鸿蒙端支持。

- 1、先查看该 JSAPI 和组件是否已在鸿蒙小程序支持，如果小程序的鸿蒙端都尚未支持，那么多端应用的鸿蒙端也是未支持，详情可查看[小程序·HarmonyOS 适配指南](https://developers.weixin.qq.com/miniprogram/dev/framework/ability/ohos)
- 2、关于原本在多端应用中就需要兼容的组件和 JSAPI，以及原本就是多端框架新增的组件和 JSAPI，那么需前往对应的组件和 JSAPI 文档查看支持的情况，如文档中有【说明：该接口已支持在鸿蒙端使用】则表示该接口或组件在鸿蒙端可用，如果出现不符合预期的情况，也可前往[社区](https://developers.weixin.qq.com/community/develop/mixflow)反馈。反之，如果文档中没有相关的说明，则表示该接口或组件在鸿蒙端尚不支持使用，可前往[社区](https://developers.weixin.qq.com/community/develop/mixflow)反馈，评估后我们将尽快推进实现。

### [#](#其他说明) 其他说明

- 关于隐私声明，鸿蒙应用无需像 Android 和 iOS 应用那般需开发者自行实现隐私弹窗，可直接使用鸿蒙应用官方的功能实现配置隐私声明即可，详情可查看[配置隐私声明（HarmonyOS 应用）](https://developer.huawei.com/consumer/cn/doc/app/agc-help-privacy-policy-app-0000002282162168)

## [#](#二、操作步骤) 二、操作步骤

### [#](#_1、下载并安装开发者工具) 1、下载并安装开发者工具

下载最新的 nightly 开发者工具（下载后，可在工具中看到鸿蒙应用相关配置，如果没有看到的话，则是开发者工具的版本不对）

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919120444806.png)

### [#](#_2、准备鸿蒙应用开发者账号) 2、准备鸿蒙应用开发者账号

准备华为开发者账号，配置证书和 profile 相关内容，可前往华为开发者官网查看[总体流程](https://developer.huawei.com/consumer/cn/doc/app/agc-help-process-0000001146716611)

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919120802715.png)

注册华为开发者账号后，即可按照下方文档一步一步完成配置。

补充说明：下面的文档指引是以【调试证书】为例子写的文档，开发者可按实际情况使用【调试证书】或者【分发证书】

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919121045251.png)

### [#](#_3、创建鸿蒙应用并配置包名) 3、创建鸿蒙应用并配置包名

- 详细操作步骤可查看：<https://developer.huawei.com/consumer/cn/doc/app/agc-help-createharmonyapp-0000001945392297>

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919120852444.png)

- 上图中的【应用包名】需要配置在多端应用控制台中
- 如果你当前的多端应用未绑定移动应用账号，那么直接点击【修改】即可将鸿蒙的包名配置进去
- 如果你当前的多端应用已绑定移动应用账号，那么你需要前往【微信开放平台 - 管理中心 - 移动应用 - 开发信息】中配置鸿蒙的包名信息

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919121131124.png)

- 配置了鸿蒙的包名后，即可在开发者工具中查看到配置的包名

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919121214238.png)

### [#](#_4、配置-project-miniapp-json) 4、配置 project.miniapp.json

#### [#](#project-miniapp-json-介绍说明) project.miniapp.json 介绍说明

- 开发者可按需配置，当前支持的鸿蒙的配置如下：

```
{
  "miniVersion": "v2",
  "name": "麦多多",
  "version": "0.0.1",
  "versionCode": 100,
  "i18nFilePath": "i18n",
  "mini-ohos": {
    "sdkVersion": "0.5.4",
    "enableDebug": true,
    "icons": {
      "foreground": "/Users/melodytu/Desktop/aaa.png",
      "background": "/Users/melodytu/Desktop/aaa.png"
    },
    "splashscreen": {
      "startWindowIcon": "/Users/melodytu/Desktop/aaa.png",
      "startWindowBackground": "#ffffff"
    },
    "privateDescriptions": {
      "APPROXIMATELY_LOCATION": "aaa",
      "LOCATION": "bbbb",
      "ACCESS_BLUETOOTH": "cccc",
      "CAMERA": "dddd",
      "MICROPHONE": "eeee"
    }
  }
}
```

上述配置分别对应的内容如下截图：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919112252776.png)

### [#](#_5、生成-p12-文件和-csr-文件) 5、生成 p12 文件和 csr 文件

- 参考下方截图的路径进行使用

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919121750302.png) ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919121832118.png)

### [#](#_6、生成证书（cer-文件）) 6、生成证书（cer 文件）

- 前往华为开发者平台，参考下方截图的路径进行使用

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919122005665.png)

- 选择调试证书（如上面所述，本文档指引是以【调试证书】为例子写的文档，开发者可按实际情况使用【调试证书】或者【分发证书】）

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919122057236.png)

### [#](#_7、注册测试设备) 7、注册测试设备

- 详细操作步骤可查看：<https://developer.huawei.com/consumer/cn/doc/app/agc-help-add-device-0000001946142249>

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919122216588.png)

- 获取 uuid 的方式如下：（需要安装华为开发者工具）

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919122257062.png)

### [#](#_8、新建-profile) 8、新建 profile

- 详细操作步骤可查看：<https://developer.huawei.com/consumer/cn/doc/app/agc-help-add-debugprofile-0000001914423102>

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919122358215.png)

### [#](#_9、新建下载-p7b-文件) 9、新建下载 p7b 文件

- 参考下方截图的路径进行使用

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919122448260.png)

- 按照下方完成配置

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919122521877.png)

### [#](#_10、通过数据线连接真机) 10、通过数据线连接真机

- 注意：要选传输文件

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20250919122613906.png)

- 将数据线和鸿蒙手机连接到开发者工具，选择鸿蒙真机。点击运行，即可构建鸿蒙应用并运行于真机之上

Incorrect translation.