# [#](#wx-login-Object-object) wx.login(Object object)

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.3.1](../../../framework/compatibility.html)
>
> 在小程序插件中使用时，需要在用户信息功能页中获得用户授权或满足一定条件后调用。否则将返回 fail。详见 [用户信息功能页](../../../framework/plugin/functional-pages/user-info.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [小程序登录](../../../framework/open-ability/login.html)、[UnionID 机制说明](../../../framework/open-ability/union-id.html)、[接口调用频率规范](../../../framework/performance/api-frequency.html)

## [#](#功能描述) 功能描述

调用接口获取登录凭证（code）。通过凭证进而换取用户登录态信息，包括用户在当前小程序的唯一标识（openid）、微信开放平台账号下的唯一标识（unionid，若当前小程序已绑定到微信开放平台账号）及本次登录的会话密钥（session\_key）等。用户数据的加解密通讯需要依赖会话密钥完成。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| timeout | number |  | 否 | 超时时间，单位ms | [1.9.90](../../../framework/compatibility.html) |
| success | function |  | 否 | 接口调用成功的回调函数 |  |
| fail | function |  | 否 | 接口调用失败的回调函数 |  |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| code | string | 用户登录凭证（有效期五分钟）。开发者需要在开发者服务器后台调用 [code2Session](https://developers.weixin.qq.com/miniprogram/dev/OpenApiDoc/user-login/code2Session.html)，使用 code 换取 openid、unionid、session\_key 等信息 |

#### [#](#object-fail-回调函数) object.fail 回调函数

##### [#](#参数-3) 参数

###### [#](#Object-err) Object err

| 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- |
| errMsg | String | 错误信息 |  |
| errno | Number | errno 错误码，错误码的详细说明参考 [Errno错误码](../../../framework/usability/PublicErrno.html) | [2.24.0](../../../framework/compatibility.html) |

## [#](#示例代码) 示例代码

```
wx.login({
  success (res) {
    if (res.code) {
      //发起网络请求
      wx.request({
        url: 'https://example.com/onLogin',
        data: {
          code: res.code
        }
      })
    } else {
      console.log('登录失败！' + res.errMsg)
    }
  }
})
```

Incorrect translation.