# [#](#wx-miniapp-registOpenURL) wx.miniapp.registOpenURL

> iOS >= 1.0.17，Android >= 1.0.8

监听进入 App 的事件，并获取参数。开发者可以监听通过 Scheme，Universal Link，微信开放标签 [wx-open-launch-app](https://developers.weixin.qq.com/doc/service/guide/h5/opentag#跳转APP：wx-open-launch-app) 的方式进入 App 的事件，并且携带参数。

## [#](#Scheme) Scheme

开发者如果希望使用 Scheme 跳入 App，则需要在 project.miniapp.json 中设置 Scheme 的名称等配置(注意，Android 和 iOS 配置位置不同，可参考下方截图)

**请使用开发者工具 1.06.2307312 及以上版本**

- **iOS: 应用配置(info.plist)下的 URL Types 配置，其中的概念请参考[苹果文档](https://developer.apple.com/documentation/xcode/defining-a-custom-url-scheme-for-your-app)**
- **Android: 其他配置 -> URL Schemes 配置，填写 scheme 字段。**

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202308032052931.png)

### [#](#配置多个-Scheme) 配置多个 Scheme

- **iOS: project.miniapp.json 切换到 JSON 格式以后，配置 additionalCFBundleURLTypes**

```
"CFBundleURLTypes": {
    "CFBundleURLName": "wechat",
    "CFBundleURLSchemes": "wechat",
    "CFBundleTypeRole": "Viewer",
    "additionalCFBundleURLTypes": [
        {
            "CFBundleURLName": "hello",
            "CFBundleURLSchemes": "hello",
            "CFBundleTypeRole": "Viewer"
        }
    ]
},
```

- **Android: project.miniapp.json 中填写 scheme 的地方，用逗号分隔填入多个即可，如 wechat,qq,miniprogram**

### [#](#使用说明) 使用说明

如填写的 scheme 为 weauth，则在安装应用后，可以在 H5 页面中，通过 href 直接调用应用

```
<a href="weauth://page/a/b?query=test">test:<a><br/>
```

说明：a 标签的写法在微信浏览器中打开不生效，需要使用微信开放标签，详情可查看 [wx-open-launch-app](1000934#跳转APP：wx-open-launch-app)

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202308091652376.png)

## [#](#Universal-Link) Universal Link

- Universal Link 仅 iOS 支持
- iOS 应用在构建时，会使用微信开放平台注册的 Universal Link，开发者需要按照苹果的官方文档配置[apple-app-site-association](https://developer.apple.com/documentation/xcode/supporting-associated-domains)等设置。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202308032100803.png)

## [#](#微信开放标签-wx-open-launch-app) 微信开放标签 wx-open-launch-app

[微信开放标签](https://developers.weixin.qq.com/doc/oplatform/Mobile_App/WeChat_H5_Launch_APP)进入多端应用底层其实依然是通过上述的方式，只是携带了自己的数据格式。

**注意：在 iOS 的情况下，因为微信开放标签底层都是基于 scheme 或 Universal Link 方式进入 App，所以会先触发 action 为其他类型的回调，再触发一次 opensdkOnRep 类型；Android 则 不会。**

## [#](#JSAPI-代码例子) JSAPI 代码例子

```
wx.miniapp.registOpenURL((param) => {
    console.log('regsitOpenUrl', param)
})
```

#### [#](#回调参数) 回调参数

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| action | string | 唤起 App 的方式：'scheme','webpageURL','opensdkOnRep' |
| data | object | 携带的详细信息 |

```
// 如果是scheme进入
const param = {
    action: 'scheme',
    data: {
        url: 'xxx',
        host: 'xxx',
        path: 'xxx',
        query: 'xxx'
    }
}
// 如果是universal link进入
const param = {
    action: 'webpageURL',
    data: {
        url: 'xxx',
        host: 'xxx',
        path: 'xxx',
        query: 'xxx'
    }
}
// 如果是微信开放标签进入
const param = {
    action: 'opensdkOnRep',
    data: 'extraInfo' // string类型透传
}
```

## [#](#直接打开-App-页面) 直接打开 App 页面

从 iOS >= 1.1.13 开始，支持 Scheme / Universal Link 打开 App 时携带对应参数直接打开 App 页面。

### [#](#配置) 配置

iOS 使用该特性开发者需在 project.miniapp.json 种按下图所示打开开关。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202311291142588.png)

### [#](#示例) 示例

#### [#](#Scheme-2) Scheme

直接在 Scheme 后拼上页面路径，如下：

```
YOUR_APP_SCHEME://pages/index/index?q=123
```

#### [#](#Universal-Link-2) Universal Link

`page` 参数指定跳转页面，注意参数需要经过 encodeURIComponent 转码，即

```
'https://dev.weixin.qq.com/app?page=' + encodeURIComponent('/pages/index/index?q=123')

->

https://dev.weixin.qq.com/app?page=%2Fpages%2Findex%2Findex%3Fq%3D123
```

#### [#](#不由-SDK-处理跳转) 不由 SDK 处理跳转

开发者在开启新特性的情况下，可以通过指定参数 `__donutDontNavigate__=true` 让 SDK 不自动处理跳转，从而保留开发者自行处理的能力。如下：

```
YOUR_APP_SCHEME://pages/index/index?q=123&__donutDontNavigate__=true

https://dev.weixin.qq.com/app?page=%2Fpages%2Findex%2Findex%3Fq%3D123&__donutDontNavigate__=true
```

## [#](#wx-miniapp-registOpenURL-2) wx.miniapp.registOpenURL

取消 wx.miniapp.registOpenURL 注册的监听函数。入参为之前注册的函数。

```
const openUrlListener = (param) => {
    console.log('regsitOpenUrl', param)
}

wx.miniapp.registOpenURL(openUrlListener)
wx.miniapp.unRegistOpenURL(openUrlListener)
```

Incorrect translation.