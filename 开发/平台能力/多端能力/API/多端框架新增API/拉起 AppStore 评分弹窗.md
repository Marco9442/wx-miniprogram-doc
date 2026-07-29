# [#](#wx-miniapp-openAppStoreRating) wx.miniapp.openAppStoreRating

> iOS >= 1.4.11

该接口用于快速拉起 AppStore 评分弹窗，方便用户在 App 内即可给 App 进行评分，无需前往 AppStore 。

### [#](#注意) 注意

1、该接口不适用于 iOS 18.0 及以上版本，开发者可通过 `wx.getSystemInfo` 接口获取系统版本号进行判断。

2、替代方案1：使用[wx.miniapp.jumpToAppStore](jumpToAppStore)代替，该接口支持前往评论打分页

3、替代方案2：开发者可自行开发 [iOS 插件](../../handbook/plugin/iosPlugin)实现该功能。

#### [#](#JSAPI-代码例子) JSAPI 代码例子

```
wx.miniapp.openAppStoreRating({
    success: (res) => {
        console.log('openAppStoreRating success:', res);
    },
    fail: (res) => {
        console.log('openAppStoreRating fail:', res);
    }
});
```

Incorrect translation.