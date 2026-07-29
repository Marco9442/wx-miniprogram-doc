# [#](#wx-weixinAppLogin) wx.weixinAppLogin

- 移动应用微信登录是一种唤起用户的微信 APP 进行登录的方式。调用 JSAPI 实现该登录方式，获取临时登录凭证 (code)。通过凭证进而换取用户标识信息等。
- 另外，登录成功后，可以调用微信 JSAPI 以使用微信开放能力，如云开发等。

注意：该接口不支持在「移动应用助手」中调试，开发者需构建 apk 或者 ipa 安装到手机后才能调试

## [#](#前置准备) 前置准备

- [多端应用账号需绑定移动应用账号](../../handbook/web/bind-openapp)
- 需要在 `project.miniapp.json` 勾选 OpenSDK

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数 |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| code | string | 用户登录凭证（有效期五分钟）。开发者可以在开发者服务器调用 [code2Verifyinfo](../../openapi/code2Verifyinfo)，使用 code 换取用户标识信息等   注意 code2Verifyinfo 用的是多端应用 appid 和 secret，不是小程序的 appid 和 secret，也不是移动应用的 appid 和 secret |

#### [#](#object-fail-回调函数) object.fail 回调函数

##### [#](#参数-3) 参数

###### [#](#Object-res-2) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errCode | number | 错误码 |
| errMsg | string | 错误提示 |

**res.errCode**

| errCode | 说明 |
| --- | --- |
| -1 | system error |
| 10001005 | 多端应用未接入身份管理 |
| 10001007 | 多端应用未绑定移动应用 |
| 10001015 | 多端应用绑定移动应用错误(如果在移动应用助手里测试这个接口，就会出现这个报错) |
| -700000 | 前端错误，errMsg 将给出详细提示 |

**常见前端错误**

| errMsg | 指引 |
| --- | --- |
| sendOpenReq:fail launch wechat fail | 拉起微信失败，即你的多端应用尚未绑定移动应用账号，导致 OpenSDK 失败了。解决方案：[绑定移动应用账号](../../handbook/web/bind-openapp) |

## [#](#示例代码) 示例代码

```
wx.weixinAppLogin({
  success (res) {
    if (res.code) {
      // 发起网络请求
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

// login 成功后，可以直接使用云开发功能
wx.cloud.callFunction({
  name: 'myCloudFunction'
})
```

Incorrect translation.