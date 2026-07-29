# [#](#获取密钥AppKey) 获取密钥AppKey

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：getAppKey

获取B2b商户号的密钥AppKey。

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/retail/B2b/getappkey?access_token=ACCESS_TOKEN
```

### [#](#云调用) 云调用

- 本接口不支持云调用。

### [#](#第三方调用) 第三方调用

- 本接口支持第三方平台代商家调用。
- 该接口所属的权限集 id 为：158
- 服务商获得其中之一权限集授权后，可通过使用 [authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/Before_Develop/call_interface) 说明文档。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| access\_token | string | 是 | ACCESS\_TOKEN | 接口调用凭证，可使用 [access\_token](../../mp-access-token/api_getaccesstoken)、[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken) |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| mchid | string | 是 | 1230000109 | 微信商户号。长度限制[1,32]。由微信支付生成并下发的商户号。 |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 示例 | 说明 |
| --- | --- | --- | --- |
| appkey | string | - | 现网AppKey。由平台生成并下发的现网应用密钥。 |
| sandbox\_appkey | string |  | 沙箱AppKey。由平台生成并下发的沙箱应用密钥。 |
| errcode | number | 0 | [错误码](#apierrcode) |
| errmsg | string | ok | [错误信息](#apierrcode) |

## [#](#_4-注意事项) 4. 注意事项

本接口无特殊注意事项

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
    "mchid": "1230000109"
}
```

返回示例

```
{
    "appkey": "xxx",
    "sandbox_appkey": "xxx",
    "errcode": 0,
    "errmsg": "OK"
}
```

## [#](#_6-错误码) 6. 错误码

此接口没有特殊错误码，可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

## [#](#_7-适用范围) 7. 适用范围

本接口暂未明确可调用账号类型，或在业务中根据调用传参自行确定是否可调用，请以实际调用情况为准。

Incorrect translation.