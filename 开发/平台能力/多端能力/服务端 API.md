# [#](#登录凭证校验) 登录凭证校验

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：code2Verifyinfo

通过 wx.xxxLogin（如 wx.weixinAppLogin、wx.appleLogin、wx.weixinMiniProgramLogin） 获得临时登录凭证 (code) 后，传到开发者服务器，开发者服务器调用本接口获取用户标识信息，可以用于构建自定义登录态。

注意：本接口需要的多端应用secret，可在多端应用控制台应用详情页查看

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
GET https://api.weixin.qq.com/donut/code2verifyinfo?access_token=ACCESS_TOKEN
```

### [#](#云调用) 云调用

- 本接口不支持云调用。

### [#](#第三方调用) 第三方调用

- 本接口不支持第三方平台调用。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| access\_token | string | 是 | ACCESS\_TOKEN | 接口调用凭证，可使用 [access\_token](getaccesstoken) |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appid | string | 是 | 多端应用 ID，在多端应用控制台应用详情页可以查看；不是小程序 Appid，也不是移动应用 Appid |
| appsecret | string | 是 | 多端应用secret，在多端应用控制台应用详情页可以查看；不是小程序 secret，也不是移动应用 secret |
| code | string | 是 | 临时登录凭证，可通过 wx.weixinAppLogin、wx.weixinMiniProgramLogin、wx.phoneSmsLogin、wx.appleLogin、[本机号码一键登录 button](../component/auth/phoneOneClickLogin) 获取 |
| grant\_type | string | 是 | 授权类型，固定值为"authorization\_code" |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | [错误码](#apierrcode) |
| errmsg | string | 错误提示 |
| login\_info | [object](#Res__login_info) | 登录信息 |
| user\_info | [object](#Res__user_info) | 用户标识信息 |

### [#](#Res-login-info-Object-Payload) Res.login\_info `Object Payload`

登录信息

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| type | string | 登录方式: weixinApp, weixinMiniProgram, phoneSms, apple, phoneOneClick |
| login\_time | number | 登录时间 |

### [#](#Res-user-info-Object-Payload) Res.user\_info `Object Payload`

用户标识信息

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| user\_id | string | 多端用户ID |
| openapp\_info | [object](#Res__user_info__openapp_info) | 微信移动应用信息 |
| miniprogram\_info | [object](#Res__user_info__miniprogram_info) | 微信小程序信息 |
| phone\_info | [object](#Res__user_info__phone_info) | 手机号信息 |
| apple\_info | [object](#Res__user_info__apple_info) | 苹果账号信息 |
| huawei\_info | [object](#Res__user_info__huawei_info) | 华为账号信息 |

### [#](#Res-user-info-openapp-info-Object-Payload) Res.user\_info.openapp\_info `Object Payload`

微信移动应用信息

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| appid | string | 微信移动应用appid |
| openid | string | 微信移动应用对应的openid |
| unionid | string | unionid |
| headimgurl | string | 用户头像，最后一个数值代表正方形头像大小（有 0、46、64、96、132 数值可选，0 代表640\*640正方形头像），用户没有头像时该项为空 |
| nickname | string | 普通用户昵称 |

### [#](#Res-user-info-miniprogram-info-Object-Payload) Res.user\_info.miniprogram\_info `Object Payload`

微信小程序信息

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| appid | string | 微信小程序appid |
| openid | string | 微信小程序对应的openid |
| unionid | string | unionid，小程序需要绑定在微信开放平台才会返回；否则为空 |

### [#](#Res-user-info-phone-info-Object-Payload) Res.user\_info.phone\_info `Object Payload`

手机号信息

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| phone | string | 手机号 |

### [#](#Res-user-info-apple-info-Object-Payload) Res.user\_info.apple\_info `Object Payload`

苹果账号信息

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| bundleid | string | 苹果应用id |
| apple\_user\_id | string | 苹果用户id |
| apple\_email | string | 苹果用户邮箱账号 |
| is\_apple\_email\_verified | boolean | 邮箱是否已验证（true/false） |
| is\_apple\_email\_private | boolean | 邮箱是否为私人邮箱（true/false） |

### [#](#Res-user-info-huawei-info-Object-Payload) Res.user\_info.huawei\_info `Object Payload`

华为账号信息

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| client\_id | string | 华为 client\_id |
| huawei\_open\_id | string | 华为 open\_id |
| huawei\_union\_id | string | 华为 union\_id |
| huawei\_display\_name | string | 华为账号昵称 |
| huawei\_picture | string | 华为账号头像 |
| huawei\_email | string | 华为账号邮箱 |
| is\_huawei\_email\_verified | boolean | 邮箱是否已验证（true/false） |
| type | string | 类型 |

## [#](#_4-注意事项) 4. 注意事项

### [#](#_4-1-账号绑定说明) 4.1 账号绑定说明

##### [#](#账号之间没有绑定) 账号之间没有绑定

- 当 type 是 weixinMiniProgram（小程序登录） 的时候返回 miniprogram\_info
- 当 type 是 weixinApp（微信登录） 的时候返回 openapp\_info
- 当 type 是 phoneSms（手机验证码登录） 和 phoneOneClick（一键本机号码登录） 的时候返回 phone\_info
- 当 type 是 apple 的时候返回 apple\_info

##### [#](#账号之间有绑定) 账号之间有绑定

- 例如，小程序登录（wx.weixinMiniProgramLogin）后通过 `wx.miniapp.bindPhone` 引导用户完成了手机号绑定，那么，当 type 是 weixinMiniProgram（小程序登录） 的时候会同时返回 miniprogram\_info 和 phone\_info
- 同理，手机登录（wx.phoneSmsLogin）后通过 `wx.miniapp.bindWeixin` 引导用户完成了微信绑定，那么，当 type 是 phoneSms（手机验证码登录） 的时候会同时返回 phone\_info 和 openapp\_info
- 以此类推，不同的登录方式之间可以引导进行账号的绑定；code2Verifyinfo 接口会依据 type 以及已绑定的账号类型情况而同时返回对应的信息

### [#](#_4-2-常问问题) 4.2 常问问题

- **Q：为什么我的返回信息中没有 phone\_info / openapp\_info？**
- A：code2Verifyinfo 接口根据开发者调用的登录方式和账号间的绑定关系来返回对应信息。

  - 场景一：账号间没有绑定关系

    比如，传入[微信小程序登录 wx.weixinMiniProgramLogin](../api/auth/wx.weixinMiniProgramLogin) 获取的 code，code2verifyinfo 将返回[微信小程序信息 miniprogram\_info](#Res__user_info__miniprogram_info)，但返回信息中不包含[微信移动应用信息 openapp\_info](#Res__user_info__openapp_info)，[手机号信息 phone\_info](#Res__user_info__phone_info)，[苹果信息 apple\_info](#Res__user_info__apple_info)
  - 场景二：账号间存在绑定关系

    比如，某用户的手机号和苹果账号绑定，如果传入其中一种登录方式获取的 code，code2verifyinfo 将同时返回[手机号信息 phone\_info](#Res__user_info__phone_info) 和[苹果信息 apple\_info](#Res__user_info__apple_info)

    开发者可以调用 [wx.miniapp.checkBindInfo](../api/auth/wx.miniapp.checkBindInfo) 检查当前用户是否已经绑定某种账号
- **Q：wx.login、wx.miniapp.login 获取的 code 可以在 code2verifyinfo 使用吗？**
- A：wx.login、wx.miniapp.login 获取的 code 不支持在 code2verifyinfo 使用。
- **Q：调用 code2verifyinfo 失败，报错为 {"errcode": 43001, "errmsg": "系统失败 rid: xxx"}，如何解决？**
- A：请使用 get 发起请求。

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
  appid: 'aaa',
  appsecret: 'bbb',
  code: 'ccc',
  grant_type: 'authorization_code'
}
```

返回示例

```
{
    "errcode": 0,
    "login_info": {
        "type": "weixinApp",
        "login_time": 12345678,
        "appid": "aaa"
    },
    "user_info": {
        "user_id": "xxx",
        "openapp_info": {
            "appid": "bbb",
            "openid": "ccc",
            "unionid": "ddd",
            "headimgurl": "HEADIMGURL",
            "nickname": "NICKNAME"
        },
        "phone_info": {
            "phone": "137xxxxxxx"
        },
        "apple_info": {
            "bundleid": "eee",
            "apple_user_id": "fff",
            "apple_email": "xxx@test.com",
            "is_apple_email_verified": false,
            "is_apple_email_private": false
        },
        "huawei_info": {
            "client_id": "6917575068155340466",
            "huawei_open_id": "AAAVXQFo5cL1lFLxQ0dhhVLvnIhlU",
            "huawei_union_id": "",
            "huawei_display_name": "over",
            "huawei_picture": "https://upfile-drcn.platform.hicloud.com/QYbytCcQAMsmzK77575068155340466.jpeg",
            "huawei_email": "",
            "is_huawei_email_verified": false,
            "type": "huawei-app"
        },
        "miniprogram_info": {
            "appid": "bbb",
            "openid": "ccc",
            "unionid": "ddd"
        }
    }
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 |
| --- | --- |
| -1 | system error |
| 10001000 | code过期 |
| 10001001 | code错误 |
| 10001002 | appid错误 |
| 10001003 | appsecret填错了，或者是参数传成了“secret”。正确的参数是“appsecret” |
| 10001004 | grant\_type错误 |
| 10001005 | 多端应用未接入身份管理 |

## [#](#_7-适用范围) 7. 适用范围

本接口支持「多端应用」账号类型调用。其他账号类型如无特殊说明，均不可调用。

Incorrect translation.