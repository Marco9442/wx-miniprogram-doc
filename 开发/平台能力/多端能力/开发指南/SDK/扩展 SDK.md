# [#](#扩展-SDK) 扩展 SDK

为缩减 SDK 的体积，基础 SDK 不包含部分扩展能力的 JSAPI，如开发者需使用对应的接口能力，需勾选对应的扩展 SDK

扩展 SDK 与 JSAPI 的对应关系可查看[SDK 使用介绍](sdk#%E4%BA%8C%E3%80%81%E4%BD%BF%E7%94%A8%E4%BB%8B%E7%BB%8D)
JSAPI 详情可查看 [API 总览](../../api/total)

## [#](#一、使用介绍) 一、使用介绍

多端应用框架中部分小程序 JSAPI 抽离成了单独的模块以减少应用打包体积，用户可根据自身需要引入所需功能。开发者可以在开发者工具通过可视化编辑项目的 `project.miniapp.json` 中 拓展 SDK 配置来设置对应的拓展模块是否使用，详情可查看 [配置文件](../config)

部分扩展 SDK 涉及收集了个人信息，如果你的应用使用了涉及收集个人信息的 JSAPI，开发者需在应用的隐私政策中详细说明，否则会被应用市场驳回；上架相关问题可以查看[上架应用市场常见问题](../../troubleshooting/publish)

补充：点此可查看[个人信息监控范围](personal)

**注意：开启配置以后需要重新构建App。**

## [#](#二、扩展-SDK-及对应的-JSAPI) 二、扩展 SDK 及对应的 JSAPI

当前支持的扩展 SDK 如下（注意，Android 与 iOS 有所区别）：

### [#](#_2-1-iOS-扩展-SDK) 2.1 iOS 扩展 SDK

| project.miniapp.json 中对应的名称 | JSAPI 分组名称 | 接口详情 |
| --- | --- | --- |
| OpenFuns SDK(不含支付) | wx.miniapp.shareXXX 相关API以及 wx.miniapp.login | [API 总览 - 转发](../../api/total#%E8%BD%AC%E5%8F%91)   [API 总览 - 登录](../../api/total#%E7%99%BB%E5%BD%95) |
| OpenFuns SDK(含支付) | wx.miniapp.shareXXX 相关API以及 wx.miniapp.login、wx.miniapp.requestPayment | [API 总览 - 转发](../../api/total#%E8%BD%AC%E5%8F%91)   [API 总览 - 登录](../../api/total#%E7%99%BB%E5%BD%95)  [API 总览 - 支付](../../api/total#%E6%94%AF%E4%BB%98) |
| Network SDK | WebSocket、mDNS、TCP 通信、UDP 通信、WIFI、网络相关API | [API 总览 - 网络 - WebSocket](../../api/total#websocket)   [API 总览 - 网络 - mDNS](../../api/total#mdns)   [API 总览 - 网络 - TCP 通信](../../api/total#tcp-%E9%80%9A%E4%BF%A1)   [API 总览 - 网络 - UDP 通信](../../api/total#udp-%E9%80%9A%E4%BF%A1)  [API 总览 - WIFI](../../api/total#wi-fi)  [API 总览 - 网络](../../api/total#%E7%BD%91%E7%BB%9C-1) |
| LBS SDK | 地图、位置相关API | [API 总览 - 媒体 - 地图](../../api/total#%E5%9C%B0%E5%9B%BE)   [API 总览 - 位置](../../api/total#%E4%BD%8D%E7%BD%AE) |
| Media SDK | 图片、视频、音频、背景音频、录音、相机相关API | [API 总览 - 媒体 - 图片](../../api/total#%E5%9B%BE%E7%89%87)   [API 总览 - 媒体 - 视频](../../api/total#%E8%A7%86%E9%A2%91)   [API 总览 - 媒体 - 音频](../../api/total#%E9%9F%B3%E9%A2%91)   [API 总览 - 媒体 - 背景音频](../../api/total#%E8%83%8C%E6%99%AF%E9%9F%B3%E9%A2%91)  [API 总览 - 媒体 - 录音](../../api/total#%E5%BD%95%E9%9F%B3)  [API 总览 - 媒体 - 相机](../../api/total#%E7%9B%B8%E6%9C%BA) |
| Bluetooth SDK | 蓝牙API | [API 总览 - 蓝牙 - 通用](../../api/total#%E8%93%9D%E7%89%99-%E9%80%9A%E7%94%A8)   [API 总览 - 蓝牙 - 低功耗中心设备](../../api/total#%E8%93%9D%E7%89%99-%E4%BD%8E%E5%8A%9F%E8%80%97%E4%B8%AD%E5%BF%83%E8%AE%BE%E5%A4%87)   [API 总览 - 蓝牙 - 低功耗外围设备](../../api/total#%E8%93%9D%E7%89%99-%E4%BD%8E%E5%8A%9F%E8%80%97%E5%A4%96%E5%9B%B4%E8%AE%BE%E5%A4%87)   [API 总览 - 蓝牙 - 信标(Beacon)](../../api/total#%E8%93%9D%E7%89%99-%E4%BF%A1%E6%A0%87-beacon) |
| Idaas SDK | 苹果登录相关API | [wx.appleLogin](../../api/auth/wx.appleLogin) |
| TPNS SDK | 消息推送相关API | [wx.miniapp.getXGPushManager](../../api/miniapp/tpnsApi)   补充：点此查看[消息推送合规指南](../../handbook/devtools/tpns#_1%E3%80%81%E5%85%B3%E4%BA%8E%E5%90%88%E8%A7%84%E6%8C%87%E5%8D%97) |
| GDT SDK | 腾讯广告相关API | [wx.miniapp.setEnableAdSplash](../../api/miniapp/setEnableAdSplash)   补充：点此查看[腾讯广告合规指南](../../handbook/devtools/ad#_2%E3%80%81%E5%85%B3%E4%BA%8E%E5%90%88%E8%A7%84%E6%8C%87%E5%8D%97) |
| Others SDK | 电话、扫码、短信相关API | [API 总览 - 电话](../../api/total#%E7%94%B5%E8%AF%9D)   [API 总览 - 扫码](../../api/total#%E6%89%AB%E7%A0%81)   [API 总览 - 短信](../../api/total#%E7%9F%AD%E4%BF%A1) |
| LBS SDK | 加速计、罗盘、设备方向、陀螺仪相关API | [API 总览 - 加速计](../../api/total#%E5%8A%A0%E9%80%9F%E8%AE%A1)   [API 总览 - 罗盘](../../api/total#%E7%BD%97%E7%9B%98)  [API 总览 - 陀螺仪](../../api/total#%E9%99%80%E8%9E%BA%E4%BB%AA)  [API 总览 - 设备方向](../../api/total#%E8%AE%BE%E5%A4%87%E6%96%B9%E5%90%91) |

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202307182332460.png)

### [#](#_2-2-Android-扩展-SDK) 2.2 Android 扩展 SDK

| project.miniapp.json 中对应的名称 | JSAPI 分组名称 | 接口详情 |
| --- | --- | --- |
| Network SDK | WebSocket、mDNS、TCP 通信、UDP 通信、WIFI、网络相关API | [API 总览 - 网络 - WebSocket](../../api/total#websocket)   [API 总览 - 网络 - mDNS](../../api/total#mdns)   [API 总览 - 网络 - TCP 通信](../../api/total#tcp-%E9%80%9A%E4%BF%A1)   [API 总览 - 网络 - UDP 通信](../../api/total#udp-%E9%80%9A%E4%BF%A1)  [API 总览 - WIFI](../../api/total#wi-fi)  [API 总览 - 网络](../../api/total#%E7%BD%91%E7%BB%9C-1) |
| LBS SDK | 地图、位置相关API | [API 总览 - 媒体 - 地图](../../api/total#%E5%9C%B0%E5%9B%BE)   [API 总览 - 位置](../../api/total#%E4%BD%8D%E7%BD%AE) |
| Media SDK | 图片、视频、音频、背景音频、录音、相机相关API | [API 总览 - 媒体 - 图片](../../api/total#%E5%9B%BE%E7%89%87)   [API 总览 - 媒体 - 视频](../../api/total#%E8%A7%86%E9%A2%91)   [API 总览 - 媒体 - 音频](../../api/total#%E9%9F%B3%E9%A2%91)   [API 总览 - 媒体 - 背景音频](../../api/total#%E8%83%8C%E6%99%AF%E9%9F%B3%E9%A2%91)  [API 总览 - 媒体 - 录音](../../api/total#%E5%BD%95%E9%9F%B3)  [API 总览 - 媒体 - 相机](../../api/total#%E7%9B%B8%E6%9C%BA) |
| Bluetooth SDK | 蓝牙API | [API 总览 - 蓝牙 - 通用](../../api/total#%E8%93%9D%E7%89%99-%E9%80%9A%E7%94%A8)   [API 总览 - 蓝牙 - 低功耗中心设备](../../api/total#%E8%93%9D%E7%89%99-%E4%BD%8E%E5%8A%9F%E8%80%97%E4%B8%AD%E5%BF%83%E8%AE%BE%E5%A4%87)   [API 总览 - 蓝牙 - 低功耗外围设备](../../api/total#%E8%93%9D%E7%89%99-%E4%BD%8E%E5%8A%9F%E8%80%97%E5%A4%96%E5%9B%B4%E8%AE%BE%E5%A4%87)   [API 总览 - 蓝牙 - 信标(Beacon)](../../api/total#%E8%93%9D%E7%89%99-%E4%BF%A1%E6%A0%87-beacon) |
| Scanner SDK | 扫码相关API | [API 总览 - 扫码](../../api/total#%E6%89%AB%E7%A0%81) |
| XWEB SDK | 画布 canvas相关API | [API 总览 - 画布](../../api/total#%E7%94%BB%E5%B8%83) |
| XWEB Embed SDK | 画布 canvas相关API | [API 总览 - 画布](../../api/total#%E7%94%BB%E5%B8%83) |
| TPNS SDK | 消息推送相关API | [wx.miniapp.getXGPushManager](../../api/miniapp/tpnsApi)   补充：点此查看[消息推送合规指南](../../handbook/devtools/tpns#_1%E3%80%81%E5%85%B3%E4%BA%8E%E5%90%88%E8%A7%84%E6%8C%87%E5%8D%97) |
| GDT SDK | 腾讯广告相关API | [wx.miniapp.setEnableAdSplash](../../api/miniapp/setEnableAdSplash)   补充：点此查看[腾讯广告合规指南](../../handbook/devtools/ad#_2%E3%80%81%E5%85%B3%E4%BA%8E%E5%90%88%E8%A7%84%E6%8C%87%E5%8D%97) |

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202307182334774.png)

## [#](#三、补充说明) 三、补充说明

### [#](#_3-1-openSDK) 3.1 openSDK

关于微信登录、微信分享、微信支付等开放能力，Android 无需额外配置扩展 SDK；iOS 则需配置 OpenFuns SDK，且区分是否包含微信支付功能的版本；若你的应用使用了微信开放能力但无支付相关功能，需勾选 OpenFuns SDK（不含支付）的版本，否则在上架 App Store 时会被驳回

OpenFuns SDK（不含支付）和 OpenFuns SDK（含支付）不可同时勾选

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202307141129521.png)

### [#](#_3-2-扫码) 3.2 扫码

如果使用了扫码的功能，iOS 应用需勾选 Others SDK

### [#](#_3-3-XWEB) 3.3 XWEB

如果使用了 canvas、echart 等功能，Android 应用需勾选 XWeb SDK；且建议勾选 XWeb Embed SDK，此版本 SDK 可在首次启动时即可加载，使得首次启动时即可正常使用 canvas、echart 等功能

补充：xweb 支持在真机使用，支持在 arm64 模拟器使用，不支持在 x86 模拟器或其他模拟器使用

XWeb SDK 和 XWeb Embed SDK 无需同时勾选，如果同时勾选效果等同于只勾选 XWeb Embed SDK

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202307141130578.png)

### [#](#_3-4-苹果支付) 3.4 苹果支付

苹果支付相关接口，无需勾选相关的扩展 SDK，按照[接口文档](../../api/miniapp/IAP)接入即可

Incorrect translation.