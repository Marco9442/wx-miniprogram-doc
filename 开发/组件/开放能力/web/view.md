开放能力/web-view/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#web-view) web-view
> 基础库 1.6.4 开始支持，低版本需做 [兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。
> \*\*小程序插件\*\*：不支持
>
> \*\*微信 Windows 版\*\*：支持
>
> \*\*微信 Mac 版\*\*：支持
>
> \*\*微信 鸿蒙 OS 版\*\*：支持
渲染框架支持情况：WebView
## [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
承载网页的容器。会自动铺满整个小程序页面， \*\*个人类型的小程序暂不支持使用。\*\*
客户端 6.7.2 版本开始， [`navigationStyle: custom`](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html) 对 [web-view](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html) 组件无效
## [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#%E5%B1%9E%E6%80%A7%E8%AF%B4%E6%98%8E) 属性说明
| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| src | string | | 否 | webview 指向网页的链接。可打开关联的公众号的文章，其它网页需登录 [小程序管理后台](https://mp.weixin.qq.com/) 配置业务域名。 | [1.6.4](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| bindmessage | eventhandler | | 否 | 网页向小程序 postMessage 时，会在以下特定时机触发并收到消息：小程序后退、组件销毁、分享、复制链接（ [2.31.1](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)）。e.detail = { data }，data是多次 postMessage 的参数组成的数组。 | [1.6.4](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| bindload | eventhandler | | 否 | 网页加载成功时候触发此事件。e.detail = { src } | [1.6.4](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| binderror | eventhandler | | 否 | 网页加载失败的时候触发此事件。e.detail = { url, fullUrl }，其中 fullUrl 为加载失败时的完整 url | [1.6.4](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#%E7%9B%B8%E5%85%B3%E6%8E%A5%E5%8F%A3-1) 相关接口 1
[web-view](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html) 网页中可使用 [JSSDK 1.3.2](https://res.wx.qq.com/open/js/jweixin-1.3.2.js) 提供的接口返回小程序页面。
支持的接口有：
| 接口名 | 说明 | 最低版本 |
| --- | --- | --- |
| wx.miniProgram.navigateTo | 参数与小程序接口一致 | [1.6.4](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| wx.miniProgram.navigateBack | 参数与小程序接口一致 | [1.6.4](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| wx.miniProgram.switchTab | 参数与小程序接口一致 | [1.6.5](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| wx.miniProgram.reLaunch | 参数与小程序接口一致 | [1.6.5](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| wx.miniProgram.redirectTo | 参数与小程序接口一致 | [1.6.5](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| wx.miniProgram.postMessage | 向小程序发送消息，会在以下特定时机触发组件的message事件：小程序后退、组件销毁、分享、复制链接（ [2.31.1](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)） | [1.7.1](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| wx.miniProgram.getEnv | 获取当前环境 | [1.7.1](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
[在开发者工具中预览效果](https://developers.weixin.qq.com/s/aRVmcimz66Yb "在开发者工具中预览效果")
```javascript
//
// javascript
wx.miniProgram.navigateTo({url: '/path/to/page'})
wx.miniProgram.postMessage({ data: 'foo' })
wx.miniProgram.postMessage({ data: {foo: 'bar'} })
wx.miniProgram.getEnv(function(res) { console.log(res.miniprogram) })
```
## [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#%E7%9B%B8%E5%85%B3%E6%8E%A5%E5%8F%A3-2) 相关接口 2
[web-view](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html) 网页中 \*\*仅支持以下 [JSSDK接口](https://mp.weixin.qq.com/wiki?t=resource/res\_main&id=mp1421141115)\*\*：
| 接口模块 | 接口说明 | 具体接口 | 鸿蒙 OS 支持情况 |
| --- | --- | --- | --- |
| 判断客户端是否支持js | | checkJSApi | ✓ |
| 图像接口 | 拍照或上传 | chooseImage | ✓ |
| | 预览图片 | previewImage | ✓ |
| | 上传图片 | uploadImage | ✓ |
| | 下载图片 | downloadImage | ✓ |
| | 获取本地图片 | getLocalImgData | ✓ |
| 音频接口 | 开始录音 | startRecord | |
| | 停止录音 | stopRecord | |
| | 监听录音自动停止 | onVoiceRecordEnd | |
| | 播放语音 | playVoice | |
| | 暂停播放 | pauseVoice | |
| | 停止播放 | stopVoice | |
| | 监听语音播放完毕 | onVoicePlayEnd | |
| | 上传接口 | uploadVoice | |
| | 下载接口 | downloadVoice | |
| 智能接口 | 识别音频 | translateVoice | |
| 设备信息 | 获取网络状态 | getNetworkType | ✓ |
| 地理位置 | 使用内置地图打开地点 | openLocation | ✓ |
| | 获取地理位置 | getLocation | ✓ |
| 摇一摇周边 | 开启ibeacon | startSearchBeacons | |
| | 关闭ibeacon | stopSearchBeacons | |
| | 监听ibeacon | onSearchBeacons | |
| 微信扫一扫 | 调起微信扫一扫 | scanQRCode | ✓ |
| 微信卡券 | 拉取使用卡券列表 | chooseCard | |
| | 批量添加卡券接口 | addCard | |
| | 查看微信卡包的卡券 | openCard | |
| 长按识别 | 小程序圆形码 | 无 | ✓ |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#%E7%9B%B8%E5%85%B3%E6%8E%A5%E5%8F%A3-3) 相关接口 3
用户分享时可获取当前 [web-view](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html) 的URL，即在`onShareAppMessage`回调中返回`webViewUrl`参数。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81-2) 示例代码
示例代码：
```javascript
Page({
onShareAppMessage(options) {
console.log(options.webViewUrl)
}
})
```
## [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#%E7%9B%B8%E5%85%B3%E6%8E%A5%E5%8F%A3-4) 相关接口 4
在网页内可通过`window.\_\_wxjs\_environment`变量判断是否在小程序环境，建议在`WeixinJSBridgeReady`回调中使用，也可以使用 [JSSDK 1.3.2](https://res.wx.qq.com/open/js/jweixin-1.3.2.js) 提供的`getEnv`接口。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81-3) 示例代码
```javascript
// web-view下的页面内
function ready() {
console.log(window.\_\_wxjs\_environment === 'miniprogram') // true
}
if (!window.WeixinJSBridge || !WeixinJSBridge.invoke) {
document.addEventListener('WeixinJSBridgeReady', ready, false)
} else {
ready()
}
// 或者
wx.miniProgram.getEnv(function(res) {
console.log(res.miniprogram) // true
})
```
## [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#%E7%9B%B8%E5%85%B3%E6%8E%A5%E5%8F%A3-5) 相关接口 5
从微信`7.0.0`开始，可以通过判断 `userAgent` 中包含 `miniProgram` 字样来判断小程序 web-view 环境。
从微信 Android `8.0.16`，iOS `8.0.17` 开始，web-view 的 `userAgent` 中会携带小程序的 appid。
对于微信鸿蒙 OS 版本，可根据 `userAgent` 中包含 `ArkWeb` 和 `MicroMessenger` 字样来判断。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81-4) 示例代码
```js
console.log(window.navigator.userAgent);
// "Mozilla/....../arm64 miniProgram/wx14211cb2fd9f805123" 携带了 miniProgram 字样和小程序的 appid
```
## [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#%E7%9B%B8%E5%85%B3%E6%8E%A5%E5%8F%A3-6) 相关接口 6
从微信`7.0.3`开始，webview内可以通过判断下面的方式判断小程序是否在前台：
```js
WeixinJSBridge.on('onPageStateChange', function(res) {
console.log('res is active', res.active)
})
```
## [\#](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html\#Bug-Tip) Bug & Tip
1. `tip`： \*\*网页内 iframe 的域名也需要配置到域名白名单。\*\*
2. `tip`：开发者工具上，可以在 [web-view](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html) 组件上通过右键 \- 调试，打开 [web-view](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html) 组件的调试。
3. `tip`：每个页面只能有一个 [web-view](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html)， [web-view](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html) 会自动铺满整个页面，并覆盖其他组件。
4. `tip`： [web-view](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html) 网页与小程序之间不支持除 JSSDK 提供的接口之外的通信。
5. `tip`：在 iOS 中，若存在JSSDK接口调用无响应的情况，可在 [web-view](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html) 的 src 后面加个#wechat\\_redirect解决。
6. `tip`：避免在链接中带有中文字符，在 iOS 中会有打开白屏的问题，建议加一下 encodeURIComponent