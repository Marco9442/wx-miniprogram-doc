# [#](#查询加密URLLink) 查询加密URLLink

[调试诊断](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_tools)

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：queryUrlLink

该接口用于查询小程序加密 url\_link 配置

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/wxa/query_urllink?access_token=ACCESS_TOKEN
```

### [#](#云调用) 云调用

- 调用方法：urllink.query
- 出入参和 HTTPS 调用相同，调用方式可查看 [云调用](https://developers.weixin.qq.com/doc/oplatform/developers/dev/cloudCall) 说明文档。

### [#](#第三方调用) 第三方调用

- 本接口支持第三方平台代商家调用。
- 该接口所属的权限集 id 为：88
- 服务商获得其中之一权限集授权后，可通过使用 [authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/Before_Develop/call_interface) 说明文档。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| access\_token | string | 是 | 接口调用凭证，可使用 [access\_token](../../mp-access-token/api_getaccesstoken)、[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken) |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url\_link | string | 否 | 小程序加密 url\_link。 |
| query\_type | number | 否 | 查询类型。默认值0，查询 url\_link 信息：0， 查询每天剩余访问次数：1 |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | [错误码](#apierrcode) |
| errmsg | string | [错误信息](#apierrcode) |
| url\_link\_info | [object](#Res__url_link_info) | url\_link 配置 |
| quota\_info | [object](#Res__quota_info) | quota 配置 |

### [#](#Res-url-link-info-Object-Payload) Res.url\_link\_info `Object Payload`

url\_link 配置

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| appid | string | 小程序 appid |
| path | string | 小程序页面路径 |
| query | string | 小程序页面query |
| create\_time | number | 创建时间，为 Unix 时间戳 |
| expire\_time | number | 到期失效时间，为 Unix 时间戳，0 表示永久生效 |
| env\_version | string | 要打开的小程序版本。正式版为"release"，体验版为"trial"，开发版为"develop" |

### [#](#Res-quota-info-Object-Payload) Res.quota\_info `Object Payload`

quota 配置

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| remain\_visit\_quota | number | URL Scheme（加密+明文）/加密 URL Link 单天剩余访问次数 |

## [#](#_4-注意事项) 4. 注意事项

本接口无特殊注意事项

## [#](#_5-代码示例) 5. 代码示例

### [#](#_5-1-查询url-link) 5.1 查询url\_link

请求示例

```
{
  "url_link": "https://wxaurl.cn/BQZRrcFCPvg?cq=a=hello",
  "query_type": 0
}
```

返回示例

```
{
  "errcode": 0,
  "errmsg": "ok",
  "url_link_info": {
    "appid": "appid",
    "path": "",
    "query": "a=hello",
    "create_time": 611928113,
    "expire_time": 0,
    "env_version": "release",
    "cloud_base": {
      "env": "",
      "doamin": "",
      "path": "",
      "query": "",
      "resource_appid": ""
    }
  }
}
```

### [#](#_5-2-查询剩余访问次数) 5.2 查询剩余访问次数

请求示例

```
{
  "query_type": 1
}
```

返回示例

{
"errcode": 0,
"errmsg": "ok",
"quota\_info": {
"remain\_visit\_quota": 1000000
}
}
}

### [#](#_5-3-云函数调用) 5.3 云函数调用

请求示例

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV,
})
exports.main = async (event, context) => {
  try {
    const result = await cloud.openapi.urllink.query({
        "urlLink": 'https://wxaurl.cn/BQZRrcFCPvg'
      })
    return result
  } catch (err) {
    return err
  }
}
```

返回示例

```
{
  "errcode": 0,
  "errmsg": "ok",
  "urlLinkInfo": {
    "appid": "appid",
    "path": "",
    "query": "",
    "createTime": 611928113,
    "expireTime": 0,
    "envVersion": "release",
    "cloudBase": {
      "env": "",
      "doamin": "",
      "path": "",
      "query": "",
      "resourceAppid": ""
    }
  }
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| -1 | system error | 系统繁忙，此时请开发者稍候再试 |
| 40097 | invalid args | 参数错误 |
| 85403 | not found | scheme/url link不存在 |

## [#](#_7-适用范围) 7. 适用范围

本接口在不同账号类型下的可调用情况：

| 小程序 | 小游戏 |
| --- | --- |
| ✔ | ✔ |

- ✔：该账号可调用此接口。
- 其他未明确声明的账号类型，如无特殊说明，均不可调用此接口。

Incorrect translation.