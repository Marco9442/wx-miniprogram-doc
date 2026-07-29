# [#](#wx-miniapp-installApp) wx.miniapp.installApp

安装应用（只适用于 Android），要安装的 apk 包名必须跟当前应用相同，生成签名的证书一致，且应用版本号不能小于当前应用。

> Android >= 1.0.13

补充：该接口可结合 [wx.getAppBaseInfo](../diffapi/getAppBaseInfo) 获取当前应用的 `appVersion` ，检测到有新版本即可使用 `wx.miniapp.installApp` 提示用户在应用内下载并安装 apk 来进行更新

注意：需在`project.miniapp.json`里勾选 `install SDK`

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202404081826795.png)

#### [#](#参数) 参数

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| filePath | string |  | 是 | 应用的用户目录 |

#### [#](#JSAPI-代码例子) JSAPI 代码例子

```
// login
wx.downloadFile({
    url: 'http://xxxx/包名.apk',
    success(res) {
        console.log('download apk success', res)
        wx.miniapp.installApp({
            filePath: res.tempFilePath,
            success(res) {
                console.log('install app success', res)
            },
            fail(res) {
                console.log('install app fail', res)
            }
        })
    },
    fail(res) {
        console.log('download apk fail', res)
    }
})
```

Incorrect translation.