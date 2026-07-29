# [#](#wx-getAppBaseInfo) wx.getAppBaseInfo

- 获取多端应用 App 基础信息
- 补充 1：SDK >= 1.3.10

### [#](#变更周知) 变更周知

- 当 SDK >= 1.4.X，新增返回 miniappId 和 moduleId，含义查看文档说明

### [#](#返回值-Object) 返回值 Object

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| enableDebug | boolean | 是否已打开调试 |
| fontSizeSetting | number | 用户字体大小（单位px） |
| fontSizeScaleFactor | number | 字体缩放倍率 |
| host | object | 宿主 App 环境信息 |
| language | string | 系统语言 |
| SDKVersion | string | 基础库版本 |

#### [#](#host) host

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| appId | string | 多端应用的 Id，不是小程序的 AppID |
| miniappId | string | 多端应用的 Id ；SDK >= 1.4.X 新增返回该字段 |
| moduleId | string | 多端应用资源包的 Id ；SDK >= 1.4.X 新增返回该字段 |
| appVersion | string | 多端 App 的应用版本，对应的值为 `project.miniapp.json` 中的 version |
| versionCode | string | App 的 versionCode（对应的值为 `project.miniapp.json` 中的 versionCode） ；Android SDK >= 1.4.8 返回；iOS >= 1.4.17 返回 |
| env | string | 运行环境，值为 "SAAASDK" |
| packageName | string | 对应 Android 应用的包名，Android 系统时返回 |
| bundleIdentifier | string | 对应 iOS 的 Bundle ID，iOS 系统时返回 |
| sdkVersion | string | SDK 版本（对应的值为 `project.miniapp.json` 中的 sdkVersion） |
| version | string | SDK 版本号数字值 |

### [#](#iOS-应用的-getAppBaseInfo-返回-language-使用的映射关系更新说明) iOS 应用的 getAppBaseInfo 返回 language 使用的映射关系更新说明

| 原始值 | 实际返回值 |
| --- | --- |
| zh-Hans | zh\_CN |
| zh-CN | zh\_CN |
| zh-Hant | zh\_TW |
| zh-TW | zh\_TW |
| zh-HK | zh\_HK |

- 其他未命中的语言统一返回系统设置的真实的 lang，例如：el-CN 返回 el

Incorrect translation.