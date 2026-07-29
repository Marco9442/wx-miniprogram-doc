设备/NFC 读写/wx.canAddSecureElementPass/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc/wx.canAddSecureElementPass.html\#wx-canAddSecureElementPass-Object-args) wx.canAddSecureElementPass(Object args)
> 基础库 3.8.5 开始支持，低版本需做 [兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。
> \*\*以 [Promise 风格](https://developers.weixin.qq.com/miniprogram/dev/framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用\*\*：不支持
>
> \*\*小程序插件\*\*：不支持
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc/wx.canAddSecureElementPass.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
判断设备是否支持添加该支付卡
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc/wx.canAddSecureElementPass.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc/wx.canAddSecureElementPass.html\#Object-args) Object args
| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| panid | String | | 是 | 支付的panid（PrimaryAccountIdentifier） |
| success | function | | 否 | 接口调用成功的回调函数 |
| fail | function | | 否 | 接口调用失败的回调函数 |
| complete | function | | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc/wx.canAddSecureElementPass.html\#args-success-%E5%9B%9E%E8%B0%83%E5%87%BD%E6%95%B0) args.success 回调函数
##### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc/wx.canAddSecureElementPass.html\#%E5%8F%82%E6%95%B0-2) 参数
###### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc/wx.canAddSecureElementPass.html\#Object-object) Object object
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| result | String | 返回值 |
| errorMsg | String | 错误信息 |