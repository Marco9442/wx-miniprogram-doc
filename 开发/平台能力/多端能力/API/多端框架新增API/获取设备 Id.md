# [#](#获取设备-id) 获取设备 id

为方便开发者获取系统的设备 id，并且考虑到获取设备 id 是属于用户的敏感信息，需开发者在应用的隐私政策中进行声明，因此平台将以官方插件的形式进行开发，开发者需按照下方指引进行引用。

### [#](#SDK-要求) SDK 要求

- Android SDK 需 >= 1.3.3
- iOS SDK >= 1.2.25

### [#](#步骤-1，前往-project-miniapp-json-配置插件) 步骤 1，前往 project.miniapp.json 配置插件

- 需将 project.miniapp.json 切换成 json 模式，然后填入下方内容

```
"mini-plugin": {
  "ios": [
    {
      "open": true,
      "pluginId": "wx033a6b34f2c7ea15", // 插件id
      "pluginVersion": "1.0.0", // 插件版本号
      "isFromLocal": false
    }
  ],
  "android": [
    {
      "open": true,
      "pluginId": "wx033a6b34f2c7ea15",
      "pluginVersion": "1.0.0"
    }
  ]
}
```

### [#](#步骤-2，前往-project-miniapp-json-配置-iOS-隐私信息访问许可) 步骤 2，前往 project.miniapp.json 配置 iOS 隐私信息访问许可

- 可将 project.miniapp.json 切换成可视化模式，iOS 端如果使用到了 IDFA 则需要配置访问许可 `NSUserTrackingUsageDescription`，需在此填写用途

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202403311700929.png)

### [#](#步骤-3，加载插件) 步骤 3，加载插件

- iOS 与 Android 的写法一样，参考如下：

```
wx.miniapp.loadNativePlugin({
  pluginId: "wx033a6b34f2c7ea15",
  success(myPlugin) {
    // 调用插件接口
  },
  fail(err) {
    // 启动插件失败
  }
})
```

### [#](#步骤-4，iOS-端获取-IDFV) 步骤 4，iOS 端获取 IDFV

```
const IDFV = myPlugin.getIdentifierForVendor()
```

### [#](#步骤-5，iOS-端获取-IDFA) 步骤 5，iOS 端获取 IDFA

```
const IDFA = myPlugin.getAdvertisingIdentifier()
```

#### [#](#补充，获取-IDFA-之前需要获取系统授权) 补充，获取 IDFA 之前需要获取系统授权

- 可参考下方方式通过 requestTrackingPermission 获得系统授权

```
myPlugin.requestTrackingPermission({}, (ret) => {
  /** 
   * ret status的枚举类型
   * ATTrackingManagerAuthorizationStatusNotDetermined
   * ATTrackingManagerAuthorizationStatusRestricted
   * ATTrackingManagerAuthorizationStatusDenied
   * ATTrackingManagerAuthorizationStatusAuthorized
   */
  if (ret && ret.status === 'ATTrackingManagerAuthorizationStatusAuthorized') {
    const IDFV = myPlugin.getIdentifierForVendor()
  }
})
```

### [#](#步骤-6，Android-端获取-Android-Id) 步骤 6，Android 端获取 Android Id

```
const ret = myPlugin.getAndroidId({})
```

Incorrect translation.