# [#](#多端应用中-wx-getSetting-兼容处理) 多端应用中 wx.getSetting 兼容处理

在小程序项目升级到多端项目后，开发者会发现 `wx.getSetting` 和 `wx.openSetting` 等与设置相关的接口无法运行。

## [#](#一、原因概述) 一、原因概述

由于多端项目在打包 App 后，运行在移动端时，本身已经脱离了微信的权限体系。开发者的项目只需要向系统（iOS 和 Android）获取权限即可。

`wx.getSetting` 和 `wx.openSetting` 是小程序运行在微信客户端时，向微信客户端申请的权限集合获取和打开管理。这两个 API 在多端 App 运行时，无法使用。

## [#](#二、改造过程) 二、改造过程

因此当我们在多端项目运行时，替换掉 `wx.getSetting` 和 `wx.openSetting` 接口。

### [#](#_2-1-触发和查看权限) 2.1 触发和查看权限

以 camera 为例子，当在多端项目中通过组件或者 API，拉起系统的摄像头时，首次会触发系统的弹窗。

![](https://res.wx.qq.com/op_res/DbIKCtlVwsk8nWb6N28hLWkht31Yq_MM0DgBpPDNPHY4893Afc2uMeiBfibLvU62dgCdxgx01R0UzM0x-yKkMw)

如果用户点击拒绝，则应用后续无法访问相机，开发者可通过 [wx.getAppAuthorizeSetting](../../api/diffapi/getAppAuthorizeSetting) 获取当前应用的权限授权情况。

**需要注意：Android 和 iOS 的权限返回有所区别，开发者需根据平台条件判断。**

[wx.getAppAuthorizeSetting](../../api/diffapi/getAppAuthorizeSetting) 返回的内容如下：

```
{
    "cameraAuthorized":"authorized", // 摄像头权限
    "locationAuthorized":"authorized", // 定位权限
    "microphoneAuthorized":"authorized", // 麦克风权限
    "notificationAuthorized":"authorized", // 通知权限
    "phoneCalendarAuthorized":"authorized", // 读写日历权限
    "locationReducedAccuracy":true, // 定位准确度（仅 iOS，true 表示模糊定位，false 表示精确定位）
    "albumAuthorized":"authorized", // 访问相册权限（仅 iOS）
    "bluetoothAuthorized":"authorized", // 蓝牙权限（仅 iOS）
    "notificationAlertAuthorized":"authorized", // 带有提醒的通知权限（仅 iOS）
    "notificationBadgeAuthorized":"authorized", // 带有标记的通知权限（仅 iOS）
    "notificationSoundAuthorized":"authorized", // 带有声音的通知权限（仅 iOS）
}
```

如果返回的内容值标记为 `not determined` 表示尚未请求授权，会在 App 下一次调用系统相应权限时自动请求。

返回的内容随着 SDK 的升级可能会有不同，在开发时请直接访问[wx.getAppAuthorizeSetting](../../api/diffapi/getAppAuthorizeSetting) 文档获取最新权限列表。

### [#](#_2-2-用户拒绝重新拉起) 2.2 用户拒绝重新拉起

如果用户明确拒绝了，即返回的权限内容值标记为 `denied`，则需要调用 [wx.openAppAuthorizeSetting](https://developers.weixin.qq.com/miniprogram/dev/api/base/system/wx.openAppAuthorizeSetting.html) 打开 App 的系统权限页，提示用户手动给予相应的权限。

```
wx.openAppAuthorizeSetting({
    success (res) {
        console.log('打开成功！')
    },
    fail(e){
        console.log('打开失败！')
    }
})
```

> 开发者工具无法打开系统权限页，需真机预览这里的实现。正因为如此，开发者工具的所有权限都是 authorized。

## [#](#三、配置隐私访问描述) 三、配置隐私访问描述

多端 App 在上架应用市场时，应用市场平台（不是微信多端平台）会对涉及用户隐私的系统权限进行审核确认。当你的应用涉及到隐私相关的 API 调用，则需要在 `project.miniapp.json` 中配置隐私访问描述。

Android 的隐私配置默认为空，上架前需按照使用需要填写。详情查看[此文档](../../handbook/devtools/auth-message)

![](https://res.wx.qq.com/op_res/pyr0LKaEgduao4FEwEiMzAhf9ja-PGz_UFeAO6DqGP0BOAxcqXNClHxavn-5H3aqq74sYkt2epWw4V1LATwH0g)

iOS 的隐私配置默认开关需要关闭，上架前需按照使用替换填写。详情查看[此文档](../../handbook/devtools/iOS-auth-message)

![](https://res.wx.qq.com/op_res/pyr0LKaEgduao4FEwEiMzEtMN1FJJt9b85tI2y-LupDGBeJG0hyKFTaPfiWH8ZJM1obKMIhXO1kvYjkctZ1NnQ)

在 iOS 中运行时，首次触发权限调用，会自动弹出申请

![](https://res.wx.qq.com/op_res/DbIKCtlVwsk8nWb6N28hLWkht31Yq_MM0DgBpPDNPHY4893Afc2uMeiBfibLvU62dgCdxgx01R0UzM0x-yKkMw)

如果应用上架审核时检测到某些权限，但是实际上你并未用到，而应用市场则以你未声明相关用途而驳回时，则可将 project.miniapp.json 切换到 json 格式，然后通过 `uselessPermissions` 参数移除相关权限项\*\*

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F%E4%BC%81%E4%B8%9A%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_4e4cb2e1-cb64-4806-ad78-d9c1f0e3d15d.png)

Incorrect translation.