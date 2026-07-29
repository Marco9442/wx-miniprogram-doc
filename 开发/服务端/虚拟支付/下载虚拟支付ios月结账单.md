# [#](#下载虚拟支付ios月结账单) 下载虚拟支付ios月结账单

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：download\_ios\_settlement\_bill

查询指定月份范围内的 iOS 结算账单列表及其下载链接。

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/xpay/download_ios_settlement_bill?access_token=ACCESS_TOKEN&pay_sig=PAY_SIG
```

### [#](#云调用) 云调用

- 本接口不支持云调用。

### [#](#第三方调用) 第三方调用

- 本接口支持第三方平台代商家调用。
- 该接口所属的权限集 id 为：157
- 服务商获得其中之一权限集授权后，可通过使用 [authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/Before_Develop/call_interface) 说明文档。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| access\_token | string | 是 | ACCESS\_TOKEN | 接口调用凭证，可使用 [access\_token](../mp-access-token/api_getaccesstoken)、[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken) |
| pay\_sig | - | 是 | - | 支付签名 |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| start\_month | string | 是 | 202601 | 开始月份，格式 YYYYMM |
| end\_month | string | 是 | 20266 | 结束月份，格式 YYYYMM |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | 错误码，0 表示成功 |
| errmsg | string | - |
| bill\_list | [objarray](#Res__bill_list<Array>) | 结算单列表 |

### [#](#Res-bill-list-Array-Object-Payload) Res.bill\_list(Array) `Object Payload`

结算单列表

| 参数名 | 类型 | 示例 | 说明 |
| --- | --- | --- | --- |
| month | string | 202501 | 月份，格式 YYYYMM |
| bill\_url | string | https://... | 账单下载链接，及时使用，一定时间后失效 |

## [#](#_4-注意事项) 4. 注意事项

本接口无特殊注意事项

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
    "start_month": "202601",
    "end_month": "20266"
}
```

返回示例

```
{
    "errcode": 0,
    "errmsg": "",
    "bill_list": [
        {
            "month": "202501",
            "bill_url": "https://..."
        }
    ]
}
```

## [#](#_6-错误码) 6. 错误码

此接口没有特殊错误码，可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

## [#](#_7-适用范围) 7. 适用范围

本接口暂未明确可调用账号类型，或在业务中根据调用传参自行确定是否可调用，请以实际调用情况为准。

Incorrect translation.