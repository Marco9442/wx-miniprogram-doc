开放接口/微信表情/wx.openStickerIPView/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/sticker/wx.openStickerIPView.html\#wx-openStickerIPView-Object-object) wx.openStickerIPView(Object object)
> 基础库 3.0.1 开始支持，低版本需做 [兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。
> \*\*以 [Promise 风格](https://developers.weixin.qq.com/miniprogram/dev/framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用\*\*：不支持
>
> \*\*小程序插件\*\*：不支持
>
> \*\*微信 鸿蒙 OS 版\*\*：支持
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/sticker/wx.openStickerIPView.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
打开表情IP合辑
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/sticker/wx.openStickerIPView.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/sticker/wx.openStickerIPView.html\#Object-object) Object object
| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| url | string | | 是 | 表情IP合辑链接，可前往 [表情开放平台](https://sticker.weixin.qq.com/cgi-bin/mmemoticon-bin/loginpage?t=login/index)，在详情页中的「小程序跳转链接」入口复制 |
| success | function | | 否 | 接口调用成功的回调函数 |
| fail | function | | 否 | 接口调用失败的回调函数 |
| complete | function | | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/sticker/wx.openStickerIPView.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
```js
wx.openStickerIPView({
url: '',
success(res) {}
})
```