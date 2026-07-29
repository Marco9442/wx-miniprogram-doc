# [#](#wx-miniapp-launchMiniProgram) wx.miniapp.launchMiniProgram

App 拉起微信小程序

说明：该接口已支持在鸿蒙端使用

## [#](#接入前注意事项) 接入前注意事项

- 能力介绍可查看 [App 拉起小程序](https://developers.weixin.qq.com/doc/oplatform/Mobile_App/Launching_a_Mini_Program/Launching_a_Mini_Program)，且由于该能力需依赖微信 Open SDK 因此需按照指引在[微信开放平台](https://open.weixin.qq.com/)创建移动应用账号，以完成相关初始化配置，详情可查看[微信移动应用能力初始化指引](../../new-capability/opensdk)

### [#](#参数) 参数

对齐[微信 opensdk 跳转小程序](https://developers.weixin.qq.com/doc/oplatform/Mobile_App/Launching_a_Mini_Program/iOS_Development_example)参数，方便理解

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| userName | string |  | 是 | 小程序原始 ID，如 gh\_d43f693ca31f，[点击查看获取方式](../../troubleshooting/dev#_1、如何获取小程序原始-id) |
| path | string | 默认拉起小程序首页 | 否 | 拉起小程序页面的可带参路径，如：传入 "?foo=bar"。 |
| miniprogramType | number | 默认为正式版 | 否 | 可选打开 0-正式版，1-开发版，2-体验版 |
| success | function |  | 是 | 获取后成功回调 |

## [#](#JSAPI-代码例子) JSAPI 代码例子

```
// login
 wx.miniapp.launchMiniProgram({
            userName: 'gh_d43f693ca31f', //小程序原始ID
            path: 'originfiles/pages/miniapp/miniapp?action=login',
            miniprogramType: 2, //0 release ，1 test, 2 preview
            success: (res) => {
                wx.showModal({
                    content: res.data,
                })
                console.log('get wx phonenumber success:', res)
            }
        })
```

## [#](#微信小程序返回-App) 微信小程序返回 App

开发者可以使用[button 标签](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/launchApp)跳转回 App。

**注意：安卓的情况下, 当 SDK 1.2.17 版本以下的情况下，开发者需要在 app-parameter 携带 App 的信息才能正常返回多端 App，细节如下。iOS 不需要。**

多端 App 在唤起微信小程序的时候，会携带 App 相关的信息，开发者可以在页面的 onLoad 函数的参数中获取到。

获取的信息需要在 button 标签的 app-parameter 中给回 App。同时可以带上开发者自己希望返回的信息。

安卓 App 如果未做上述操作，可能会出现报错：`sendOpenReq failed:fail opensdk failed 并没有通过微信返回多端App。`

```
onLoad(res) {  
    // Page对应onLoad函数中获取App带过来的信息
    transitiveData = res;

    // App带过来的信息需要将transitiveData作为key，同时可以在data带上开发者自己的数据。
    const data = {
        data: "MsgBackToApp",
        transitiveData
    };

    // 将需要的信息设置到data中，让button标签可以获取到
    this.setData({
        dataStr: JSON.stringify(data)
    });
}
```

```
<button open-type="launchApp" app-parameter="{{dataStr}}" bindtap="tap">
返回App
</button>
```

## [#](#常见问题) 常见问题

### [#](#_1-跳小程序了，但是返回不了-App) 1. 跳小程序了，但是返回不了 App

- 出现这种情况原因是该多端应用所绑定的移动应用账号尚未配置好 iOS 的 Bundle Id 信息或者 Android 的包名
- 举个例子，开发者创建移动应用账号的时候只配置了 iOS 的 Bundle Id 信息并且将该移动应用绑定了多端应用，使得 iOS 端跳小程序功能正常；但是该移动应用的 Android 的包名还没有配置，于是就会出现了 Android 端跳到了小程序，但是无法返回 App
- 因此，开发者需按照[移动应用创建指南文档](../../handbook/web/open_application_create)将移动应用的 iOS 的 Bundle Id 信息和 Android 的包名都配置好

Incorrect translation.