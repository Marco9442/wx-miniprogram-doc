# [#](#创建退货ID) 创建退货ID

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：addReturnId

商家在同意用户退货之后，通过本接口创建退货ID，shop\_order\_id和退货 ID 一一对应。平台根据退货 ID 下发模板消息给用户，提醒用户退货。“一个订单需要多次退货”的场景，可以在商家内部 1 个退货订单号映射多个shop\_order\_id。注：该接口中文相关的字段用UTF-8。

提醒退货通知：商家创建退货 ID 时，平台会自动下发模板消息给用户，提醒用户退货。

如有开发问题或建议，可前往[微信开放社区-微信物流服务](https://developers.weixin.qq.com/community/minihome/mixflow/1792207662500118536) 发帖提问讨论，官方工作人员会及时回复。

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/cgi-bin/express/delivery/no_worry_return/add?access_token=ACCESS_TOKEN
```

### [#](#云调用) 云调用

- 本接口不支持云调用。

### [#](#第三方调用) 第三方调用

- 本接口支持第三方平台代商家调用。
- 该接口所属的权限集 id 为：45
- 服务商获得其中之一权限集授权后，可通过使用 [authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/Before_Develop/call_interface) 说明文档。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| access\_token | string | 是 | ACCESS\_TOKEN | 接口调用凭证，可使用 [access\_token](../../mp-access-token/api_getaccesstoken)、[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken) |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shop\_order\_id | string | 是 | 商家内部系统使用的退货编号 |
| biz\_addr | [object](#Body__biz_addr) | 是 | 商家退货地址 |
| user\_addr | [object](#Body__user_addr) | 否 | 用户购物时的收货地址 |
| openid | string | 是 | 退货用户的openid |
| order\_path | string | 是 | 退货订单在商家小程序的path。如投保时已传入订单商品信息，则以投保时传入的为准 |
| goods\_list | [objarray](#Body__goods_list<Array>) | 是 | 退货商品list，一个元素为对象的数组,结构如下↓ 如投保时已传入订单商品信息，则以投保时传入的为准 |
| order\_price | number | 是 | 退货订单的价格 |
| wx\_pay\_id | string | 是 | 填写已投保的微信支付单号 |

### [#](#Body-biz-addr-Object-Payload) Body.biz\_addr `Object Payload`

商家退货地址

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 发/收件人姓名，不超过64字节 |
| tel | string | 是 | 发/收件人座机号码，若不填写则必须填写 mobile，不超过32字节 |
| mobile | string | 是 | 发/收件人手机号码，若不填写则必须填写 tel，不超过32字节 |
| company | string | 是 | 发/收件人公司名称，不超过64字节 |
| post\_code | string | 是 | 发/收件人邮编，不超过10字节 |
| country | string | 是 | 发/收件人国家，不超过64字节 |
| province | string | 是 | 发/收件人省份，比如："广东省"，不超过64字节 |
| city | string | 是 | 发/收件人市/地区，比如："广州市"，不超过64字节 |
| area | string | 是 | 发/收件人区/县，比如："海珠区"，不超过64字节 |
| address | string | 是 | 发/收件人详细地址，比如："XX路XX号XX大厦XX"，不超过512字节 |

### [#](#Body-user-addr-Object-Payload) Body.user\_addr `Object Payload`

用户购物时的收货地址

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 否 | 发/收件人姓名，不超过64字节 |
| tel | string | 否 | 发/收件人座机号码，若不填写则必须填写 mobile，不超过32字节 |
| mobile | string | 否 | 发/收件人手机号码，若不填写则必须填写 tel，不超过32字节 |
| company | string | 否 | 发/收件人公司名称，不超过64字节 |
| post\_code | string | 否 | 发/收件人邮编，不超过10字节 |
| country | string | 否 | 发/收件人国家，不超过64字节 |
| province | string | 否 | 发/收件人省份，比如："广东省"，不超过64字节 |
| city | string | 否 | 发/收件人市/地区，比如："广州市"，不超过64字节 |
| area | string | 否 | 发/收件人区/县，比如："海珠区"，不超过64字节 |
| address | string | 否 | 发/收件人详细地址，比如："XX路XX号XX大厦XX"，不超过512字节 |

### [#](#Body-goods-list-Array-Object-Payload) Body.goods\_list(Array) `Object Payload`

退货商品list，一个元素为对象的数组,结构如下↓ 如投保时已传入订单商品信息，则以投保时传入的为准

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 退货商品的名称 |
| url | string | 是 | 退货商品图片的url |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | [错误码](#apierrcode) |
| errmsg | string | [错误信息](#apierrcode) |
| return\_id | string | 退货ID |

## [#](#_4-注意事项) 4. 注意事项

本接口无特殊注意事项

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
    "shop_order_id": "xxx",//商家内部系统使用的退货编号
    "biz_addr": {  //商家退货地址，必填
        "name": "张三",
        "mobile": "13600000000",//仅支持输入一个联系方式
        "country": "中国",
        "province": "广东省",
        "city": "广州市",
        "area": "海珠区",
        "address": "xx路 xx 号"
    },
    "user_addr": { //用户购物时的收货地址，选填
        "name": "李四",
        "mobile": "13600000000",
        "country": "中国",
        "province": "广东省",
        "city": "广州市",
        "area": "海珠区",
        "address": "xx路 xx 号"
     },
     "openid":"xxx",//退货用户的openid，用于给用户下发模版消息，通过模版消息用户可以选择退货方式
	 "order_path":"xxx",//退货订单在商家小程序的path
	 "goods_list":[
		{
			"name":"xxx",//退货商品的名称
			"url":"xxx"//退货商品图片的url
		}
	 ],
	 "order_price":1//退货订单的价格
}
```

返回示例

```
{
  "errcode": 0,
  "errmsg": "OK",
  "return_id": "1935761508265738242"
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 |
| --- | --- |
| -1 | 请联系微信平台解决 |
| 40097 | order\_id为空或者退货地址为空或者wx\_pay\_id为空 |
| 9300522 | shop\_order\_id 已存在 |
| 9300569 | wx\_pay\_id 为空 |
| 9300570 | 该微信支付单号填写错误或未投保 |

## [#](#_7-适用范围) 7. 适用范围

本接口暂未明确可调用账号类型，或在业务中根据调用传参自行确定是否可调用，请以实际调用情况为准。

Incorrect translation.