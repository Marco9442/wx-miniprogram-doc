# [#](#查询rid信息) 查询rid信息

[调试诊断](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_tools)

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：getRidInfo

本接口用于查询调用服务端接口报错返回的rid详情信息，辅助开发者高效定位问题。

适用的账号类型如下：公众号/服务号/小程序/小游戏/微信小店/带货助手/视频号助手/联盟带货机构/移动应用/网站应用/多端应用/第三方平台。

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/cgi-bin/openapi/rid/get?access_token=ACCESS_TOKEN
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
| rid | string | 是 | 调用接口报错返回的rid |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | 返回码 |
| errmsg | string | [错误信息](#apierrcode) |
| request | [object](#Res__request) | 该rid对应的请求详情 |

### [#](#Res-request-Object-Payload) Res.request `Object Payload`

该rid对应的请求详情

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| invoke\_time | number | 发起请求的时间戳 |
| cost\_in\_ms | number | 请求毫秒级耗时 |
| request\_url | string | 请求的URL参数 |
| request\_body | string | post请求的请求参数 |
| response\_body | string | 接口请求返回参数 |
| client\_ip | string | 接口请求的客户端ip |

## [#](#_4-注意事项) 4. 注意事项

1、由于查询rid信息属于开发者私密行为，因此仅支持同账号的查询。举个例子，rid=1111，是小程序账号A调用某接口出现的报错，那么则需要使用小程序账号A的access\_token调用当前接口查询rid=1111的详情信息，如果使用小程序账号B的身份查询，则出现报错，错误码为xxx。公众号、第三方平台账号等账号的接口同理。

2、如果是第三方服务商代公众号/服务号/小程序/小游戏/微信小店/带货助手/视频号助手查询调用 api返回的rid，则使用同一账号的[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken)调用即可。

3、rid的有效期只有7天，即只可查询最近7天的rid，查询超过7天的rid会出现报错，错误码为76001

4、”/xxx/sns/xxx“这类接口不支持使用该接口，会出现76022报错。

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
  "rid": "61725984-6126f6f9-040f19c4"
}
```

返回示例

```
{
  "errcode": 0,
  "errmsg": "ok",
  "request": {
    "invoke_time": 1635156704,
    "cost_in_ms": 30,
    "request_url": "access_token=50_Im7xxxx",
    "request_body": "",
    "response_body": "{\"errcode\":45009,\"errmsg\":\"reach max api daily quota limit rid: 617682e0-09059ac5-34a8e2ea\"}",
    "client_ip": "113.xx.70.51"
  }
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| 0 | ok | ok |
| 76001 | rid not found | rid不存在 |
| 76002 | rid is error | rid为空或者格式错误 |
| 76003 | could not query this rid,no permission | 当前账号无权查询该rid，该rid属于其他账号调用所产生 |
| 76004 | rid time is error | rid过期，仅支持持续7天内的rid |

## [#](#_7-适用范围) 7. 适用范围

本接口在不同账号类型下的可调用情况：

| 小程序 | 公众号 | 服务号 | 小游戏 | 微信小店 | 联盟带货机构 | 带货助手 | 小店供货商 | 第三方平台 | 移动应用 | 网站应用 | 视频号助手 | 多端应用 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | 〇 | ✔ | ✔ | ✔ | ✔ |

- ✔：该账号可调用此接口。
- 〇：第三方平台可使用 [component\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/ComponentAccessToken) 调用，是否支持代商家调用需看本文档 [调用方式](#apicalltype) 部分。

Incorrect translation.