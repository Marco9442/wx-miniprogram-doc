# [#](#wx-checkSession-Object-object) wx.checkSession(Object object)

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持

> 相关文档: [小程序登录](../../../framework/open-ability/login.html)、[接口调用频率规范](../../../framework/performance/api-frequency.html)

## [#](#功能描述) 功能描述

检查登录态 session\_key 是否过期。

session\_key 具有唯一性，在使用小程序时，同一用户在同一时刻仅有一个有效的 session\_key。

通过 wx.login 接口获得的用户登录态拥有一定的时效性。用户越久未使用小程序，用户登录态越有可能过期。反之如果用户一直在使用小程序，则用户登录态一直保持有效。具体时效逻辑由微信维护，对开发者透明。除了过期失效外，触发获取临时登录凭证 code 的操作（[小程序登录](../../../framework/open-ability/login.html) 和 [数据预拉取](../../../framework/ability/pre-fetch.html)）可能会生成新的登录态session\_key，从而使旧的 session\_key 被顶替而失效。

开发者可以调用 wx.checkSession 接口检测用户登录态是否过期。**注意，wx.checkSession 的校验对象是最后一次获取 code 操作对应的登录态 session\_key**，调用成功说明该 session\_key 未过期，调用失败说明 session\_key 已过期。如果要校验指定的 session\_key 是否有效，可以在开发者服务器后台调用 [checkSessionKey]((user-login/checkSessionKey))。

登录态失效后开发者可以再调用 wx.login 获取新的用户登录态。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
wx.checkSession({
  success () {
    //session_key 未过期，并且在本生命周期一直有效
  },
  fail () {
    // session_key 已经失效，需要重新执行登录流程
    wx.login() //重新登录
  }
})
```

Incorrect translation.