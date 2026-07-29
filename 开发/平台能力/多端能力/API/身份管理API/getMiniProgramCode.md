# [#](#wx-getMiniProgramCode) wx.getMiniProgramCode

[唤起微信小程序登录](wx.weixinMiniProgramLogin)成功后，即可调用 wx.getMiniProgramCode 获取微信临时登录凭证 ([`小程序code`](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/login/wx.login.html#功能描述))，从而实现快速适配 `wx.login`，详细的使用指南可查看[快速接入小程序登录服务](../../quickstart/auth)。

## [#](#前置准备) 前置准备

- [多端应用账号需绑定移动应用账号](../../handbook/web/bind-openapp)
- 需要在 `project.miniapp.json` 勾选 OpenSDK
- <wx.weixinMiniProgramLogin>调用成功，即唤起微信小程序登录成功

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
| code | string | 用户登录凭证（有效期五分钟）。开发者可以在开发者服务器调用[小程序登录凭证校验](https://developers.weixin.qq.com/miniprogram/dev/server/API/user-login/api_code2session)，获取到 openid、unionid 等信息 |

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
| 10001011 | 系统登录态无效 |
| 10001014 | 登录校验失败，请检查是否完成唤起微信小程序登录 |
| -700000 | 前端错误，errMsg 将给出详细提示 |

**常见前端错误**

| errMsg | 指引 |
| --- | --- |
| 无系统登录态并且缺失系统登录页 | 查看 [miniprogramLoginPath](../../handbook/devtools/auth) 配置是否正确 |
| sendOpenReq:fail launch wechat fail | 拉起微信失败，即你的多端应用尚未绑定移动应用账号，导致 OpenSDK 失败了。解决方案：[绑定移动应用账号](../../handbook/web/bind-openapp) |

## [#](#示例代码) 示例代码

```
// 前置条件：多端应用登录的唤起微信小程序登录成功。

// 获取小程序code
wx.getMiniProgramCode({
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
      console.log('获取小程序 code 失败！' + res.errMsg)
    }
  }
})
```

Incorrect translation.