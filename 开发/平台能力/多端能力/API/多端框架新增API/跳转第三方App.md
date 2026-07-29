# [#](#wx-miniapp-openUrl) wx.miniapp.openUrl

> iOS >= 1.0.30，Android >= 1.0.19

跳转第三方 App，使用接口跳转前需要在多端应用控制台上进行相关配置，具体参考[操作指南](../../handbook/web/thirdapp)。

- 说明：url 如果是 https，则是使用系统默认浏览器进行打开，而此功能无需在多端应用控制台进行配置

#### [#](#参数) 参数

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| url | string |  | 是 | 跳转的目标 App 路径，该参数的 Scheme 的前缀需与在多端应用控制台配置的一致 |

#### [#](#JSAPI-代码例子) JSAPI 代码例子

```
wx.miniapp.openUrl({
    url: "weixin://dl/moments",
    success(res) {
        console.log('wx.miniapp.openUrl success', res)
    },
    fail(err) {
        console.log('wx.miniapp.openUrl fail', err)
    }
})
```

Incorrect translation.