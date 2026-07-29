# [#](#wx-getAppAuthorizeSetting) wx.getAppAuthorizeSetting

- 获取 App 授权设置。即开发者可以通过该接口判断用户已将哪些权限授权给 App 了。
- 注意： Android 和 iOS 是有些区别的，`not determined` 值只有 iOS 会返回，Android 是没有的。
- `'not determined'` 表示尚未请求授权，会在 App 下一次调用系统相应权限时请求

## [#](#返回值) 返回值

### [#](#Android) Android

| 属性 | 返回值 | 说明 | Android 原生权限 |
| --- | --- | --- | --- |
| cameraAuthorized | 'authorized'/'denied' | 允许 App 使用摄像头的权限开关 | CAMERA |
| locationAuthorized | 'authorized'/'denied' | 允许 App 使用定位的权限开关 | ACCESS\_FINE\_LOCATION |
| microphoneAuthorized | 'authorized'/'denied' | 允许 App 使用麦克风的权限开关 | RECORD\_AUDIO |
| notificationAuthorized | 'authorized'/'denied' | 允许 App 通知的权限开关 | / |
| phoneCalendarAuthorized | 'authorized' | 允许 App 读写日历的权限开关 | 添加日历当前不涉及系统授权，所以统一返回 'authorized' |
| mediaAudioAuthorized | 'authorized'/'denied' | 允许 App 读取音频文件的权限开关 | READ\_MEDIA\_AUDIO   `targetSdkVersion` 33 以下 读的是 READ\_EXTERNAL\_STORAGE |
| mediaImagesAuthorized | 'authorized'/'denied' | 允许 App 读取图像文件的权限开关 | READ\_MEDIA\_IMAGE   `targetSdkVersion` 33 以下 读的是 READ\_EXTERNAL\_STORAGE |
| mediaVideoAuthorized | 'authorized'/'denied' | 允许 App 读取视频文件的权限开关 | READ\_MEDIA\_VIDEO   `targetSdkVersion` 33 以下 读的是 READ\_EXTERNAL\_STORAGE |
| albumAuthorized | 'undefined' | 仅 iOS 有效，所以返回 'undefined', Android 端可忽略 | / |
| albumAddOnlyAuthorized | 'undefined' | 仅 iOS 有效，所以返回 'undefined', Android 端可忽略 | / |
| bluetoothAuthorized | 'undefined' | 仅 iOS 有效，所以返回 'undefined', Android 端可忽略 | / |
| locationReducedAccuracy | 'undefined' | 仅 iOS 有效，所以返回 'undefined', Android 端可忽略 | / |
| notificationAlertAuthorized | 'undefined' | 仅 iOS 有效，所以返回 'undefined', Android 端可忽略 | / |
| notificationBadgeAuthorized | 'undefined' | 仅 iOS 有效，所以返回 'undefined', Android 端可忽略 | / |
| notificationSoundAuthorized | 'undefined' | 仅 iOS 有效，所以返回 'undefined', Android 端可忽略 | / |

- 使用到上述提及的权限，开发者需在开发者工具 - `project.miniapp.json` 中配置权限用途，才会出现授权申请的弹窗。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202406111631202.png)

### [#](#iOS) iOS

| 属性 | 返回值 | 说明 |
| --- | --- | --- |
| albumAuthorized | 'authorized'/'denied'/'not determined' | 允许 App 使用相册的权限开关 |
| albumAddOnlyAuthorized | 'authorized'/'denied'/'not determined' | 允许 App 只读相册的权限开关 |
| bluetoothAuthorized | 'not determined' | 允许 App 使用蓝牙的权限开关 |
| cameraAuthorized | 'authorized'/'denied'/'not determined' | 允许 App 使用摄像头的权限开关 |
| locationAuthorized | 'authorized'/'denied'/'not determined' | 允许 App 使用定位的权限开关 |
| locationReducedAccuracy | boolean | 定位准确度。true 表示模糊定位，false 表示精确定位 |
| microphoneAuthorized | 'authorized'/'denied'/'not determined' | 允许 App 使用麦克风的权限开关 |
| notificationAuthorized | 'authorized'/'denied' | 允许 App 通知的权限开关 |
| notificationAlertAuthorized | 'authorized'/'denied' | 允许 App 通知带有提醒的权限开关 |
| notificationBadgeAuthorized | 'authorized'/'denied' | 允许 App 通知带有标记的权限开关 |
| notificationSoundAuthorized | 'authorized'/'denied' | 允许 App 通知带有声音的权限开关 |
| phoneCalendarAuthorized | 'authorized'/'denied'/'not determined' | 允许 App 读写日历的权限开关 |

- 使用到上述提及的权限，开发者需在开发者工具 - `project.miniapp.json` 中配置权限用途，才会出现授权申请的弹窗。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202406111636319.png)

## [#](#示例代码) 示例代码

```
const appAuthorizeSetting = wx.getAppAuthorizeSetting()

console.log(appAuthorizeSetting.albumAuthorized)
console.log(appAuthorizeSetting.bluetoothAuthorized)
console.log(appAuthorizeSetting.cameraAuthorized)
console.log(appAuthorizeSetting.locationAuthorized)
console.log(appAuthorizeSetting.locationReducedAccuracy)
console.log(appAuthorizeSetting.microphoneAuthorized)
console.log(appAuthorizeSetting.notificationAlertAuthorized)
console.log(appAuthorizeSetting.notificationAuthorized)
console.log(appAuthorizeSetting.notificationBadgeAuthorized)
console.log(appAuthorizeSetting.notificationSoundAuthorized)
console.log(appAuthorizeSetting.phoneCalendarAuthorized)
```

Incorrect translation.