# [#](#查询API调用额度) 查询API调用额度

[调试诊断](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_tools)

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：getApiQuota

本接口用于查询服务端接口的的每日调用接口的额度，调用次数，频率限制。

适用账号类型：公众号/服务号/小程序/小游戏/微信小店/带货助手/视频号助手/联盟带货机构/移动应用/网站应用/多端应用/第三方平台等接口

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/cgi-bin/openapi/quota/get?access_token=ACCESS_TOKEN
```

> **支持加密请求：** 本接口支持服务通信二次加密和签名，可有效防止数据篡改与泄露。[查看详情](../../getting_started/api_signature)

### [#](#云调用) 云调用

- 本接口不支持云调用。

### [#](#第三方调用) 第三方调用

- 本接口支持第三方平台使用 [component\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/ComponentAccessToken) 自己调用，同时还支持代商家调用。
- 服务商获得任意权限集授权后，即可通过使用 [authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/Before_Develop/call_interface) 说明文档。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| access\_token | string | 是 | 接口调用凭证，可使用 [access\_token](../mp-access-token/api_getaccesstoken)、[component\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getcomponentaccesstoken)、[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken) |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cgi\_path | string | 是 | api的请求地址，例如"/cgi-bin/message/custom/send";不要前缀“https://api.weixin.qq.com” ，也不要漏了"/",否则都会76003的报错 |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | 返回码 |
| errmsg | string | [错误信息](#apierrcode) |
| quota | [object](#Res__quota) | quota详情 |
| rate\_limit | [object](#Res__rate_limit) | 普通调用频率限制 |
| component\_rate\_limit | [object](#Res__component_rate_limit) | 代调用频率限制 |

### [#](#Res-quota-Object-Payload) Res.quota `Object Payload`

quota详情

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| daily\_limit | number | 当天该账号可调用该接口的次数 |
| used | number | 当天已经调用的次数 |
| remain | number | 当天剩余调用次数 |

### [#](#Res-rate-limit-Object-Payload) Res.rate\_limit `Object Payload`

普通调用频率限制

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| call\_count | number | 周期内可调用数量，单位 次 |
| refresh\_second | number | 更新周期，单位 秒 |

### [#](#Res-component-rate-limit-Object-Payload) Res.component\_rate\_limit `Object Payload`

代调用频率限制

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| call\_count | number | 周期内可调用数量，单位 次 |
| refresh\_second | number | 更新周期，单位 秒 |

## [#](#_4-注意事项) 4. 注意事项

1、如果查询的api属于公众号的接口，则需要用公众号的 access\_token；如果查询的api属于小程序的接口，则需要用[小程序的access\_token](../mp-access-token/api_getaccesstoken)；如果查询的接口属于第三方平台的接口，则需要用[第三方平台的component\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getcomponentaccesstoken)；如此类推。

2、如果查询的接口属于第三方平台接口但用于公众号/小程序，则需要用第三方平台的[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken)

2、如果是第三方服务商代公众号/服务号/小程序/微信小店/带货助手/视频号助手查询的接口，则需要用[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken)

3、每个接口都有调用次数限制，请开发者合理调用接口。

4、”/xxx/sns/xxx“这类接口不支持使用该接口，会出现76022报错。

5、如果接口文档中有单独的说明接口的特殊的 quota 数量以及逻辑，则以每个接口的接口文档的描述为准。

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
  "cgi_path": "/wxa/gettemplatedraftlist"
}
```

返回示例

```
{
  "errcode": 0,
  "errmsg": "ok",
  "quota": {
    "daily_limit": 0,
    "used": 0,
    "remain": 0
  }
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| 0 | ok | ok |
| 76021 | cgi\_path not found, please check | cgi\_path填错了 |
| 76022 | could not use this cgi\_path，no permission | 当前调用接口使用的token与api所属账号不符，详情可看注意事项的说明 |

## [#](#_7-适用范围) 7. 适用范围

本接口在不同账号类型下的可调用情况：

| 小程序 | 公众号 | 服务号 | 小游戏 | 微信小店 | 联盟带货机构 | 带货助手 | 小店供货商 | 第三方平台 | 移动应用 | 网站应用 | 视频号助手 | 多端应用 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | 〇 | ✔ | ✔ | ✔ | ✔ |

- ✔：该账号可调用此接口。
- 〇：第三方平台可使用 [component\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/ComponentAccessToken) 调用，是否支持代商家调用需看本文档 [调用方式](#apicalltype) 部分。

Incorrect translation.