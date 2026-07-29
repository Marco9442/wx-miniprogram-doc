# [#](#wx-getSystemInfo) wx.getSystemInfo

- 本接口文档同适用于 wx.getSystemInfoAsync
- 获取系统信息，返回的 [host](#host) 信息中的 AppID 是多端应用的 AppID，并非小程序的 AppID

### [#](#变更周知) 变更周知

- 当 SDK >= 1.4.X，新增返回 miniappId 和 moduleId，含义查看文档说明

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数参数) object.success 回调函数参数

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| brand | string | 设备品牌 |
| model | string | 设备型号 |
| pixelRatio | number | 设备像素比 |
| screenWidth | number | 屏幕宽度，单位px |
| screenHeight | number | 屏幕高度，单位px |
| windowWidth | number | 可使用窗口宽度，单位px |
| windowHeight | number | 可使用窗口高度，单位px |
| statusBarHeight | number | 状态栏的高度，单位px |
| system | string | 操作系统及版本 |
| platform | string | android 表示 Android App；ios表示iOS App |
| SDKVersion | string | 基础库版本 |
| benchmarkLevel | string | 设备性能等级 |
| safeArea | Object | 在竖屏正方向下的安全区域 |
| locationReducedAccuracy | boolean | `true` 表示模糊定位，`false` 表示精确定位，仅 iOS 支持 |
| theme | string | 系统当前主题，取值为`light`或`dark`，全局配置`"darkmode":true`时才能获取，否则为 undefined （不支持小游戏） |
| [host](#host) | Object | 当前应用运行的宿主环境 |
| enableDebug | boolean | 是否已打开调试 |
| deviceOrientation | string | 设备方向 |
| errMsg | string | 错误信息，新增返回 |
| abi | string | 新增返回，Android 设备的CPU类型 |

#### [#](#host) host

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| env | string | 运行环境，值为 "SAAASDK" |
| appId | string | 多端应用的 Id，不是小程序的 AppID |
| miniappId | string | 多端应用的 Id ；SDK >= 1.4.X 新增返回该字段 |
| moduleId | string | 多端应用资源包的 Id ；SDK >= 1.4.X 新增返回该字段 |
| version | string | SDK 版本串 |
| packageName | string | 对应 Android 应用的包名，Android 系统时返回 |
| bundleIdentifier | string | 对应 iOS 的 Bundle ID，iOS 系统时返回 |
| appVersion | string | App 应用版本 |
| versionCode | string | App 的 versionCode ；Android SDK >= 1.4.8 返回；iOS >= 1.4.17 返回 |
| sdkVersion | string | SDK 版本 |

## [#](#wx-getSystemInfoSync) wx.getSystemInfoSync

返回内容同 wx.getSystemInfoAsync 的 [object.success 回调函数参数](#objectsuccess-回调函数参数)

### [#](#iOS-应用的-wx-getSystemInfo-返回-language-使用的映射关系更新说明) iOS 应用的 wx.getSystemInfo 返回 language 使用的映射关系更新说明

| 原始值 | 实际返回值 |
| --- | --- |
| zh-Hans | zh\_CN |
| zh-CN | zh\_CN |
| zh-Hant | zh\_TW |
| zh-TW | zh\_TW |
| zh-HK | zh\_HK |

- 其他未命中的语言统一返回系统设置的真实的 lang，例如：el-CN 返回 el

Incorrect translation.