# [#](#查询退货ID状态) 查询退货ID状态

[调试诊断](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_tools)

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：getReturnId

本接口用于商家查询用户退货状态（是否填写退货信息）及追踪用户退货物流，方便仓库收货。通过本接口查询退货 ID 状态，其中 status 是退货 ID 状态，order\_status是退货 ID 对应的用户运单号的状态。

如有开发问题或建议，可前往[微信开放社区-微信物流服务](https://developers.weixin.qq.com/community/minihome/mixflow/1792207662500118536) 发帖提问讨论，官方工作人员会及时回复。

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/cgi-bin/express/delivery/no_worry_return/get?access_token=ACCESS_TOKEN
```

### [#](#云调用) 云调用

- 本接口不支持云调用。

### [#](#第三方调用) 第三方调用

- 本接口支持第三方平台代商家调用。
- 该接口所属的权限集 id 为：45、85
- 服务商获得其中之一权限集授权后，可通过使用 [authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/Before_Develop/call_interface) 说明文档。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| access\_token | string | 是 | ACCESS\_TOKEN | 接口调用凭证，可使用 [access\_token](../../mp-access-token/api_getaccesstoken)、[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken) |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| return\_id | string | 是 | 退货ID |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | [错误码](#apierrcode) |
| errmsg | string | [错误信息](#apierrcode) |
| status | number | 退货方式，0.用户未填写退货信息 1.预约上门取件 2.填写自行寄回运单号 |
| waybill\_id | string | 运单号 |
| order\_status | number | 物流信息，0.已下单待揽件 1.已揽件 2.运输中 3.派件中 4.已签收 5.异常 6.代签收 7.揽收失败 8.签收失败（拒收，超区） 11.已取消 13.退件中 14.已退件 99.未知 |
| delivery\_id | string | 运力公司编码 |
| delivery\_name | string | 运力公司名称 |

## [#](#_4-注意事项) 4. 注意事项

本接口无特殊注意事项

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
    "return_id": "1935761508265738242"
}
```

返回示例

```
{
    "errcode": 0,
    "errmsg": "OK",
    "status": "1",
    "waybill_id": "JDxxxxxx",
    "order_status": 0, 
    "delivery_name": "申通快递",
    "delivery_id": SF
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 |
| --- | --- |
| -1 | 请联系微信平台解决 |
| 40097 | return\_id为空 |
| 931023 | 运单不存在 |

## [#](#_7-适用范围) 7. 适用范围

本接口暂未明确可调用账号类型，或在业务中根据调用传参自行确定是否可调用，请以实际调用情况为准。

Incorrect translation.