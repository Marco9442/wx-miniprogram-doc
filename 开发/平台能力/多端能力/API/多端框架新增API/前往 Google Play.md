# [#](#wx-miniapp-jumpToGooglePlay) wx.miniapp.jumpToGooglePlay

该接口用于跳至当前 App 的 GooglePlay 下载页

> Android SDK >= 1.3.24

注意：App 需上架 Google Play 后方可调用此接口

## [#](#接口详情) 接口详情

### [#](#参数) 参数

| **属性** | **类型** | **默认值** | **必填** | **说明** |
| --- | --- | --- | --- | --- |
| success | function |  | 是 | 获取后成功回调 |

### [#](#返回参数) 返回参数

| **属性** | **类型** | **说明** |
| --- | --- | --- |
| errcode | number | 错误码 |
| errMsg | string | 错误提示 |

### [#](#JSAPI-代码例子) JSAPI 代码例子

```
wx.miniapp.jumpToGooglePlay({
    success: (res) => {
        // 跳转成功
        console.log('jumpToGooglePlay success:', res)
    },
   fail: (res) => {
        // 本机未安装 Google Play
        console.log('jumpToGooglePlay fail:', res)
    }
})
```

Incorrect translation.