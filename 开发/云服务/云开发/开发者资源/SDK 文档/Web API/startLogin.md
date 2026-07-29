# [#](#Cloud-startLogin-options-Object) [Cloud](../Cloud).startLogin(options: Object)

> 支持端：[Web 1.1.0](../../reference/changelog-web-sdk)

web 中发起网页授权登录

## [#](#参数) 参数

### [#](#options-Object) options: Object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| provider | string |  | 是 | 授权提供方，必填 OfficialAccount （公众号） |
| appid | string |  | 是 | 公众号 AppID |
| scope | string |  | 是 | 授权 scope，比如 snsapi\_base、snsapi\_userinfo |
| redirectUri | string |  | 是 | 网页授权重定向 URL |

## [#](#使用说明) 使用说明

调用，会进行网页重定向，开始网页授权流程。

## [#](#示例代码) 示例代码

```
cloud.startLogin({
  provider: 'OfficialAccount',
  appid: '', // 公众号 AppID
  scope: 'snsapi_base', // snsapi_base 或 snsapi_userinfo
  redirectUri: ``, // 网页授权重定向 URL
})
```

Incorrect translation.