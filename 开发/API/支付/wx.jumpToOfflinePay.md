# [#](#wx-jumpToOfflinePay-Object-object) wx.jumpToOfflinePay(Object object)

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持

## [#](#功能描述) 功能描述

跳转到线下支付页面。

请求参数说明：

1. 商户需注册具有支付权限的公众号，获取 appId
2. 签名方式目前仅支持 SHA1，签名规则与公众号支付一致
3. queryStr 为 JSON 格式字符串（需 urlencode），包含 biz\_scene、recommend\_bank\_type、recommend\_bind\_serial 等字段

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| appId | string |  | 是 | 公众号 ID，商户注册具有支付权限的公众号成功后即可获得 |
| timeStamp | string |  | 是 | 时间戳，从 1970 年 1 月 1 日 00:00:00 至今的秒数，即当前的时间 |
| nonceStr | string |  | 是 | 随机字符串，长度为 32 个字符以下 |
| package | string |  | 是 | 扩展字符串，需要带入商户号信息，例如：mch\_id=123456789 |
| signType | string |  | 是 | 签名方式，目前仅支持 SHA1 |
| paySign | string |  | 是 | 签名，具体签名方案参照微信公众号支付帮助文档 |
| queryStr | string |  | 是 | JSON 格式字符串（需 urlencode），包含 biz\_scene、recommend\_bank\_type、recommend\_bind\_serial |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

Incorrect translation.