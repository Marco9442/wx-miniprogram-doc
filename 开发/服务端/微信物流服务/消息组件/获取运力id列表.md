# [#](#获取运力id列表) 获取运力id列表

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：get\_delivery\_list

商户使用此接口获取所有运力id的列表

如有开发问题或建议，可前往[微信开放社区-微信物流服务](https://developers.weixin.qq.com/community/minihome/mixflow/1792207662500118536) 发帖提问讨论，官方工作人员会及时回复。

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/cgi-bin/express/delivery/open_msg/get_delivery_list?access_token=ACCESS_TOKEN
```

### [#](#云调用) 云调用

- 本接口不支持云调用。

### [#](#第三方调用) 第三方调用

- 本接口支持第三方平台代商家调用。
- 该接口所属的权限集 id 为：45、120-121、142
- 服务商获得其中之一权限集授权后，可通过使用 [authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/Before_Develop/call_interface) 说明文档。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| access\_token | string | 是 | ACCESS\_TOKEN | 接口调用凭证，可使用 [access\_token](../../mp-access-token/api_getaccesstoken)、[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken) |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

无

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | [错误码](#apierrcode) |
| errmsg | string | [错误信息](#apierrcode) |
| delivery\_list | [object](#Res__delivery_list) | delivery\_list |
| count | number | 运力公司个数 |

### [#](#Res-delivery-list-Object-Payload) Res.delivery\_list `Object Payload`

delivery\_list

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| delivery\_id | string | 运力公司 id |
| delivery\_name | string | 运力公司名称 |

## [#](#_4-注意事项) 4. 注意事项

本接口无特殊注意事项

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{}
```

返回示例

```
{
    "errcode": 0,
    "delivery_list": [
      {
          "delivery_id": "(AU)",
          "delivery_name": "Interparcel"
      },
      {
          "delivery_id": "BDT",
          "delivery_name": "八达通"
      },
      {
          "delivery_id": "YD",
          "delivery_name": "韵达速递"
      },
      ...
    ],
    "count": 1379
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| -1 | system error | 系统繁忙，此时请开发者稍候再试 |
| 40003 | invalid openid | 不合法的 OpenID ，请开发者确认 OpenID （该用户）是否已关注公众号，或是否是其他公众号的 OpenID |
| 9300507 | invalid token  can't decryption ordecryption result is different from the plaintext | waybill\_token参数错误 |
| 9300513 | out of quota | 调用次数达到上限 |
| 9300534 | invalid shop args | access\_token与openid参数不匹配 |
| 9300559 | waybill not exist | 运单不存在 |
| 9300560 | 达到修改次数上限 |  |

## [#](#_7-适用范围) 7. 适用范围

本接口暂未明确可调用账号类型，或在业务中根据调用传参自行确定是否可调用，请以实际调用情况为准。

Incorrect translation.