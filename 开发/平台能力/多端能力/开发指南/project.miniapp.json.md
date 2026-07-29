# [#](#project-miniapp-json-配置文件) project.miniapp.json 配置文件

将小程序项目升级为多端项目后，开发者可前往 `project.miniapp.json` 进一步完成多端应用的配置（此文件是多端项目专有的），具体包含：

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
      "CAMERA": "dddd"
    }
  },
  "mini-android": {
    "resourcePath": "miniapp/android/nativeResources",
    "sdkVersion": "1.5.2",
    "toolkitVersion": "0.11.0",
    "useExtendedSdk": {
      "media": false,
      "bluetooth": false,
      "network": false,
      "scanner": false,
      "xweb": false,
      "open": false,
      "nfc": false
    },
    "icons": {
      "hdpi": "",
      "xhdpi": "",
      "xxhdpi": "",
      "xxxhdpi": ""
    },
    "splashscreen": {
      "hdpi": "",
      "xhdpi": "",
      "xxhdpi": ""
    },
    "enableVConsole": "open",
    "privacy": {
      "enable": true,
      "template": "111",
      "contentViewImage": "222",
      "cancelButtonImage": "333",
      "confirmButtonImage": "444",
      "enableViewOnly": true
    },
    "usePluginSdk": {
      "map": "1.2.5"
    },
    "privateDescriptions": {
      "ACCESS_COARSE_LOCATION": "aa",
      "ACCESS_FINE_LOCATION": "bb",
      "CAMERA": "cc",
      "POST_NOTIFICATIONS": "dd",
      "READ_CONTACTS": "ee",
      "READ_PHONE_STATE": "ff",
      "RECORD_AUDIO": "gg",
      "READ_EXTERNAL_STORAGE": "hh",
      "WRITE_EXTERNAL_STORAGE": "ii",
      "READ_MEDIA_IMAGES": "jj",
      "READ_MEDIA_VIDEO": "kk",
      "READ_MEDIA_AUDIO": "ll",
      "READ_MEDIA_VISUAL_USER_SELECTED": "mm"
    }
  },
  "mini-ios": {
    "sdkVersion": "1.6.8",
    "toolkitVersion": "0.0.9",
    "useExtendedSdk": {
      "WeAppOpenFuns": true,
      "WeAppNetwork": false,
      "WeAppBluetooth": false,
      "WeAppMedia": false,
      "WeAppLBS": false,
      "WeAppOthers": false,
      "WeAppLive": true
    },
    "enableVConsole": "close",
    "icons": {
      "mainIcon120": "",
      "mainIcon180": "",
      "spotlightIcon80": "",
      "spotlightIcon120": "",
      "settingsIcon58": "",
      "settingsIcon87": "",
      "notificationIcon40": "",
      "notificationIcon60": "",
      "appStore1024": ""
    },
    "splashScreen": {
      "customImage": ""
    },
    "privacy": {
      "enable": true,
      "template": "11",
      "contentViewImage": "22",
      "cancelButtonImage": "33",
      "confirmButtonImage": "44",
      "enableViewOnly": true
    },
    "enableOpenUrlNavigate": true,
    "privateDescriptions": {
      "NSPhotoLibraryUsageDescription": "11",
      "NSCameraUsageDescription": "22",
      "NSMicrophoneUsageDescription": "33",
      "NSLocationWhenInUseUsageDescription": "44",
      "NSLocationAlwaysUsageDescription": "55",
      "NSLocationAlwaysAndWhenInUseUsageDescription": "66",
      "NSContactsUsageDescription": "77",
      "NSCalendarsUsageDescription": "88",
      "NSRemindersUsageDescription": "99",
      "NSBluetoothPeripheralUsageDescription": "10",
      "NSBluetoothAlwaysUsageDescription": "11",
      "NSSpeechRecognitionUsageDescription": "12",
      "NSLocalNetworkUsageDescription": "13",
      "NSSystemAdministrationUsageDescription": "14",
      "NSPhotoLibraryAddUsageDescription": "15"
    },
    "officialPlugins": {
      "imPush": {
        "enable": false
      }
    },
    "buildCloud": {
      "useRemote": false
    },
    "liveInfo": {
      "weAppLiveLicenseUrl": "aaa"
    }
  }
}
```

为方便开发者进行「可视化」的操作，可在右上角点击图标将「源码模式」切换为「可视化界面模式」。

![](https://res.wx.qq.com/op_res/0JglF6_aTJKf3q8UWNsCFL4i9SF383rM4RZx9GHDKNtW9mk12sSsd43p44utFCMvUjcJxkbVSUIyPg-d9S6vYg)

其他说明：如遇到问题可前往[社区](https://developers.weixin.qq.com/community/minihome/mixflow/2889188691586351105)反馈，或者联系[小助手](https://developers.weixin.qq.com/community/personal/oCJUswzW6Jdy9Iyn4fJHItBzvLXg)加入官方技术交流群进行反馈。

## [#](#一、多端应用配置) 一、多端应用配置

开发者可在 `project.miniapp.json` 配置多端应用的基础信息。

1、「应用名称 · name」指的是将应用安装至手机后，在手机桌面所展示的「App 名称」。

- 升级多端项目时，开发者工具默认获取开发者在多端应用控制台创建多端应用时填写的名称作为「应用名称」，若在此处修改后，将以此处修改的为准。

2、「应用版本名称 · version」的填写格式为：数字的三段式，例如 1.1.0。（可通过 wx.getAppBaseInfo 接口获取）

3、「应用版本号 · versionCode」必须是整数，且版本升级时要高于上一次设置的值。（可通过 wx.getAppBaseInfo 接口获取）

4、「多语言适配」用于配置多语言适配的文件夹路径，使用方法可查看[多语言适配](../handbook/devtools/localization)。

![](https://res.wx.qq.com/op_res/LUJiVmgoCRPXTJqlCeeW6a_qV2QfkVYFQfHaMTWO2hByNJa430f3Zg_tkUu6D8nkKmQGhpSpkSe5aZuakYcMqA)

## [#](#二、SDK-版本) 二、SDK 版本

在 `project.miniapp.json` 文件中，前往 Android/iOS 对应的「SDK 版本」处填入对应的版本号即可生效。

- Android SDK 更新日志可查看：[Android 更新日志](../changelog/android/changelog)。
- iOS SDK 更新日志可查看：[iOS 更新日志](../changelog/ios/changelog)。
- iOS 端若需同时兼容 iPad，请在此处勾选「启用 iPad」。
- 此外，可在微信开发者工具的「菜单栏 - 工具 - SDK 版本检测」处检查是否有新版本的 SDK，若有，可立即更新。

![](https://res.wx.qq.com/op_res/LUJiVmgoCRPXTJqlCeeW6XjVRFNH70nOJ0vOZ92_vC3ZMNqpikOl3E2fUabl6RnXaUOrMrlVDlA98cNbqvlv5A) ![](https://res.wx.qq.com/op_res/LUJiVmgoCRPXTJqlCeeW6abTpUZR2zeRAuhkYm-p9rfkoikNfk7nkv7Rdq9nIqHEIx1x9QfjjubZksLbCBYwdQ)

## [#](#三、CPU-类型) 三、CPU 类型

Android 应用上架至不同的应用市场时，对于上传的 APK 包有不同的要求：32 位安装包、64位安装包、32/64 位兼容安装包。

开发者可通过勾选下方配置构建对应的安装包。

![](https://res.wx.qq.com/op_res/LUJiVmgoCRPXTJqlCeeW6azSa_H5e8_c-WqQduwZ1FEX_UetniFMB0oPp2QitqeQVHA45fieMha8QaHE-1-k6Q)

说明：

- 勾选 armeabi-v7a 将构建 32 位安装包
- 勾选 arm64-v8a 将构建 64 位安装包
- 同时勾选，则构建的是 32/64 位兼容安装包
- 均未勾选，则默认构建 64 位安装包

## [#](#四、调试模式配置) 四、调试模式配置

可在此处配置构建的 Android/iOS 多端应用是否开启 `vConsole`。

更多详细规则说明可查看 [vConsole](vconsole)。

![](https://res.wx.qq.com/op_res/YsVXgxWAquHM6zewM1If7z5tIkUuWo_yYZLm5PKjKPYUxtBH-gQR0PSgINl8vl0KWdAsoZM4vUeLtOvgYRniTQ) ![](https://res.wx.qq.com/op_res/YsVXgxWAquHM6zewM1If7xmgKIrOtfjoAp7y1OdEPtUPvcEqSYUp4V6zBl45HUUOki23Vuld8Go6aDMs9LczZg)

## [#](#五、扩展-SDK-配置) 五、扩展 SDK 配置

为缩减 SDK 的体积，基础 SDK 不包含部分扩展能力的 JSAPI，若开发者需使用扩展的接口能力，需勾选对应的扩展 SDK。

扩展 SDK 与 JSAPI 详情可查看 [API 总览](../api/total)。

关于 LBS SDK 详情可查看[位置服务使用指南](../handbook/devtools/lbs)。

关于 GDT SDK 详情可查看[腾讯优量汇广告使用指南](../handbook/devtools/ad)。

更多 SDK 详细规则说明可查看[扩展 SDK](sdk/extend)。

![](https://res.wx.qq.com/op_res/LUJiVmgoCRPXTJqlCeeW6VzLQFwk21b0Hj6zT42xZSUdLTJql5oML1Pf7GqC_YV98fcOuqo3GakeXn1__HoHYg) ![](https://res.wx.qq.com/op_res/LUJiVmgoCRPXTJqlCeeW6WR8zs53cT1A3mhszKuW-lE8mXQmdOh9pktjbhveGLcibS_TadX8gVl3bFtiPh-f3w)

```
{
  "mini-android": {
    "sdkVersion": "1.5.2", // Android SDK 版本
    "useExtendedSdk": {
      "media": false,
      "bluetooth": false,
      "network": false,
      "scanner": false,
      "xweb": false,
      "open": false,
      "nfc": false
    }
  },
  "mini-ios": {
    "sdkVersion": "1.6.8", // iOS SDK 版本
    "useExtendedSdk": {
      "WeAppOpenFuns": true,
      "WeAppNetwork": false,
      "WeAppBluetooth": false,
      "WeAppMedia": false,
      "WeAppLBS": false,
      "WeAppOthers": false,
      "WeAppLive": true
    }
  }
}
```

## [#](#六、官方插件) 六、官方插件

可在此处配置多端应用所需的官方插件。

目前已支持的插件为「消息推送」，更多详细规则说明可查看[消息推送使用指南](../handbook/devtools/impush)。

![](https://res.wx.qq.com/op_res/YsVXgxWAquHM6zewM1If7wsKUbOQ3nWyYTtuola7dOsZiZ4QeI_1xt8wfBjR5RrEB3u--lDaxwWQURG5pzAqMA) ![](https://res.wx.qq.com/op_res/YsVXgxWAquHM6zewM1If76XjuSDnAg--WOZEAQn34UBn8ZEs0qq1i0bWo7jmvAYQiA0X1jvODi5kJq7NMmecbQ)

## [#](#七、应用图标) 七、应用图标

在 `project.miniapp.json` 文件中，前往 Android/iOS 对应的「图标配置」处，填入符合尺寸规范的图标路径即可完成图标配置。

此处的「图标」指的是将应用安装至手机后，在手机桌面所展示的「App 图标」。

注意：Android 应用和 iOS 应用的图标尺寸有所不同，请按照开发工具提示的尺寸规范填写。

![](https://res.wx.qq.com/op_res/pb_0aS36fAymqQ27EbS4Rica_r685tXfYLlEY4mGJOA8Mo0AP3sb3gJuuPHe6uO8hI6hSQPN6Blw-VEjZvncmw) ![](https://res.wx.qq.com/op_res/pb_0aS36fAymqQ27EbS4RrqW1x7fOGmzOcqDX3PoNzaRyBaetCIJVsEo-ttthuAcEq8KqxdI4or1Puy_RSqi-w)

```
{
  "miniVersion": "v2",
  "name": "麦多多",// 应用名称
  "version": "0.0.1", // 应用版本名称
  "versionCode": 100, // 应用版本号
  "i18nFilePath": "i18n",
  "mini-android": {
    "icons": {
      "hdpi": "",
      "xhdpi": "",
      "xxhdpi": "",
      "xxxhdpi": ""
    }
  },
  "mini-ios": {
    "icons": {
      "mainIcon120": "",
      "mainIcon180": "",
      "spotlightIcon80": "",
      "spotlightIcon120": "",
      "settingsIcon58": "",
      "settingsIcon87": "",
      "notificationIcon40": "",
      "notificationIcon60": "",
      "appStore1024": ""
    }
  }
}
```

## [#](#八、App-启动页配置) 八、App 启动页配置

在 `project.miniapp.json` 文件中，前往 Android/iOS 对应的「启动界面配置」，填入符合尺寸规范的图片路径即可完成启动页配置。

此处的「启动界面」指的是 App 启动时所呈现的启动页，启动页加载完成后才进入应用的首页。

注意：Android 应用和 iOS 应用的启动页尺寸有所不同，请按照开发工具提示的尺寸规范填写。

![](https://res.wx.qq.com/op_res/YsVXgxWAquHM6zewM1If70aTOleJ_F8ki-FiN5KJrDyobn8rLb2Fyh_xXu3MvrnGP2oRP-_UeTdYgYcLVqQrVw) ![](https://res.wx.qq.com/op_res/YsVXgxWAquHM6zewM1If79oxejfiTKpBBFalau2DGBOxRReveeJGDsVbuUkWg-bJvH31iqmMjzWRJASd_tURrw)

## [#](#九、隐私政策提示框配置) 九、隐私政策提示框配置

在 `project.miniapp.json` 文件中，前往 Android/iOS 对应的「隐私政策提示框配置」，勾选并填入内容配置文件路径即可。

此处的「隐私政策提示框」指的是应用启动运行时，弹出的用于说明用户数据采集行为的隐私政策协议。

详细的使用指南可查看[隐私政策提示框配置](../handbook/devtools/privacy)。

![](https://res.wx.qq.com/op_res/m-ziQJjWZThRanb6SPJod9B6xAl65AXgLYlJBx_f5OejdzA00DVcTg9goZWS5gMZdmrIuLZfpv5ayNGCdiNtpQ) ![](https://res.wx.qq.com/op_res/m-ziQJjWZThRanb6SPJod4SQTABmK921-B53-7jIe7GWEKRKmeSLXRGhuTI24ZoAi1s4mAqxG91bHVTyjqlNCg)

```
{
  "mini-android": {
    "privacy": {
      "enable": true,
      "template": "111",
      "contentViewImage": "222",
      "cancelButtonImage": "333",
      "confirmButtonImage": "444",
      "enableViewOnly": true
    }
  },
  "mini-ios": {
    "privacy": {
      "enable": true,
      "template": "11",
      "contentViewImage": "22",
      "cancelButtonImage": "33",
      "confirmButtonImage": "44",
      "enableViewOnly": true
    }
  }
}
```

## [#](#十、Android-权限描述配置) 十、Android 权限描述配置

根据工业和信息化部关于开展 App 侵害用户权益专项整治要求，应用的隐私政策中需详细描述使用权限的用途。

为方便开发者配置使用权限的用途描述，开发者可在此处进行配置。

详情可查看 [Android 系统权限配置指南](../handbook/devtools/auth-message)。

![](https://res.wx.qq.com/op_res/m-ziQJjWZThRanb6SPJod6tfxfFxW_EUxGgWpzmibJBFMWv3TpAnS0dM7OC26Yl_0Q2-uZbtTYPX8cLlfiGWpg)

```
{
  "mini-android": {
    "privateDescriptions": {
      "ACCESS_COARSE_LOCATION": "aa",
      "ACCESS_FINE_LOCATION": "bb",
      "CAMERA": "cc",
      "POST_NOTIFICATIONS": "dd",
      "READ_CONTACTS": "ee",
      "READ_PHONE_STATE": "ff",
      "RECORD_AUDIO": "gg",
      "READ_EXTERNAL_STORAGE": "hh",
      "WRITE_EXTERNAL_STORAGE": "ii",
      "READ_MEDIA_IMAGES": "jj",
      "READ_MEDIA_VIDEO": "kk",
      "READ_MEDIA_AUDIO": "ll",
      "READ_MEDIA_VISUAL_USER_SELECTED": "mm"
    }
  }
}
```

## [#](#十一、iOS-隐私信息访问许可描述) 十一、iOS 隐私信息访问许可描述

在 `project.miniapp.json` 文件中，前往「iOS - 隐私信息访问许可描述」可完成 iOS 的隐私信息访问许可描述。

「许可描述」指的是 App 在请求获取用户授予某个权限时的用途描述。

详情可查看 [iOS 隐私信息访问许可描述](../handbook/devtools/iOS-auth-message)。

![](https://res.wx.qq.com/op_res/m-ziQJjWZThRanb6SPJody8mmqOZ94XRncbAd4xlOpXF6jPwlfo-j5n9blE7HFpVs0EsOXfzJrv2UPolfNC-5w)

```
{
  "mini-ios": {
    "privateDescriptions": {
      "NSPhotoLibraryUsageDescription": "11",
      "NSCameraUsageDescription": "22",
      "NSMicrophoneUsageDescription": "33",
      "NSLocationWhenInUseUsageDescription": "44",
      "NSLocationAlwaysUsageDescription": "55",
      "NSLocationAlwaysAndWhenInUseUsageDescription": "66",
      "NSContactsUsageDescription": "77",
      "NSCalendarsUsageDescription": "88",
      "NSRemindersUsageDescription": "99",
      "NSBluetoothPeripheralUsageDescription": "10",
      "NSBluetoothAlwaysUsageDescription": "11",
      "NSSpeechRecognitionUsageDescription": "12",
      "NSLocalNetworkUsageDescription": "13",
      "NSSystemAdministrationUsageDescription": "14",
      "NSPhotoLibraryAddUsageDescription": "15"
    }
  }
}
```

## [#](#十二、内置菜单唤起配置) 十二、内置菜单唤起配置

为了更好地定位关于 SDK 的异常反馈，我们提供了通过使用 SDK 菜单栏将 SDK 运行日志上传至官方后台的能力。

开发者可在此处配置是否开启「内置菜单唤起配置」，开启后，则可通过对应的手势在 App 端唤起相关菜单并进行日志上传，详情可查看[上传 SDK 运行日志](../handbook/build/upload-log)。

## [#](#十三、Android-其他常用设置) 十三、Android 其他常用设置

在此处可配置 Android 应用的其他信息。

- 「URL Schemes」配置后可实现从其他 App 打开当前 App。监听该事件可参考接口 [registOpenURL](../api/miniapp/registOpenURL)。
- 「targetSdkVersion」用于配置应用适配的 Android 版本（API等级）。详情可查看 [Android 设置 targetSdkVersion](../handbook/devtools/targetsdkversion)。
- 「minSdkVersion」用于配置应用运行所需最低 API 级别的整数。若系统的 API 级别低于该属性中指定的值，Android 系统将阻止用户安装应用。该配置默认值为 21，请勿填写低于 21 的值。
- 「资源文件配置」用于配置需要添加在项目 app 目录下的原生资源文件路径，一般配合 Android 插件使用，详情可查看 [Android 配置原生资源](../handbook/devtools/android-native-resource)。

![](https://res.wx.qq.com/op_res/TIit8SQCvzzEYPPJPGe6VyFb0fGmG33r7Y7COAqnMI9SiwLsnMXz6G5p18sKzvs6YE0oh98wJESSoW5GWrmxvw)

## [#](#十四、iOS-Open-URL-打开-App-支持页面跳转配置) 十四、iOS Open URL 打开 App 支持页面跳转配置

勾选该配置后，通过 Universal Links/URL Scheme 打开 App 时可携带参数自动跳转 App 页面。详情可查看[监听进入 App 的事件](../api/miniapp/registOpenURL)。

![](https://res.wx.qq.com/op_res/YsVXgxWAquHM6zewM1If70qjiaM4qqHRpUlzTuptqy_RvhbD4BUgK1WjqchP-wRX8BpIEAQ4RH7oSd0QANd87g)

## [#](#十五、iOS-应用配置（info-plist-相关）) 十五、iOS 应用配置（info.plist 相关）

开发者可在此处进行 iOS 应用 `info.plist` 的相关配置。

![](https://res.wx.qq.com/op_res/YsVXgxWAquHM6zewM1If77wBHXLvw3HstxmozcJtobAWGyEAiYSxy7LkC2Mxa8Yb2RWBx-Ek0R1A9Y1F0JZEnA)

开发者还可以自定义 info.plist的 key/value。
切换project.miniapp.json到json格式, 然后在 mini-ios 下添加 customInfoPlist 的 key，然后值为object。
在object内即可定义key/value，最终会被设置到info.plist中。

**注意：框架同样会设置 info.plist 的配置，其优先级高于 customInfoPlist 的配置，即同名的key会被覆盖。**

![](https://res.wx.qq.com/op_res/rrzWLDXvV9OvvEWl51AQXEWDlW9crpKZxLp8skHpa4hPgBE8nHqsr_1QzxbB5EKlD2v4o0aQhpsNKN2gTTtnZw)

## [#](#十六、多端插件配置) 十六、多端插件配置

开发者可在此处配置多端应用所使用的 Android/iOS 插件。详情可查看[多端应用插件使用指引](../handbook/plugin/plugin_guidelines)。

![](https://res.wx.qq.com/op_res/-ro8i2M2xlANalSh13ZcIuRhGhzFNddcmvr7xDVxb8TKJMkwQiFLis3W6ccsKAtPsvO850usWEpLL_NHpP4nJw)

Incorrect translation.