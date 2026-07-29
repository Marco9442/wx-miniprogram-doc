# [\#](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/web/Cloud.getJSSDKSignature.html\#Cloud-getJSSDKSignature-options-Object-Promise-Object) [Cloud](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/Cloud).getJSSDKSignature(options: Object): Promise
> 支持端： [Web 1.1.0](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference/changelog-web-sdk)
web 中使用 SDK 登录之后可用此方法获取用于 wx.config 的 JSSDK 签名
## [\#](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/web/Cloud.getJSSDKSignature.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/web/Cloud.getJSSDKSignature.html\#options-Object) options: Object
| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| url | string | | 是 | 要签名的网页 URL |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/web/Cloud.getJSSDKSignature.html\#%E8%BF%94%E5%9B%9E%E5%80%BC) 返回值
### [\#](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/web/Cloud.getJSSDKSignature.html\#Promise-Object) Promise.
result
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| timestamp | number | 时间戳，wx.config 需用 |
| nonceStr | string | 随机串，wx.config 需用 |
| signature | string | 签名，wx.config 需用 |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/web/Cloud.getJSSDKSignature.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
```js
const res = await cloud.getJSSDKSignature({
url: '要签名的网页 URL'
})
wx.config({
appId: '公众号 AppID', // 必填，公众号的唯一标识
timestamp: res.timestamp + '', // 必填，生成签名的时间戳
nonceStr: res.nonceStr, // 必填，生成签名的随机串
signature: res.signature,// 必填，签名
jsApiList: ['JS API 名'] // 必填，需要使用的JS接口列表
})
```