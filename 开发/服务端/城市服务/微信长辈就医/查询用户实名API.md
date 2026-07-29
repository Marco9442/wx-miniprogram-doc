# [#](#查询用户实名API) 查询用户实名API

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：cityservice\_getmedrealname

查询老年患者实名信息

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/cityservice/getmedrealname?access_token=ACCESS_TOKEN
```

### [#](#云调用) 云调用

- 本接口不支持云调用。

### [#](#第三方调用) 第三方调用

- 本接口支持第三方平台代商家调用。
- 该接口所属的权限集 id 为：134
- 服务商获得其中之一权限集授权后，可通过使用 [authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/Before_Develop/call_interface) 说明文档。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| access\_token | string | 是 | ACCESS\_TOKEN | 接口调用凭证，可使用 [access\_token](../../mp-access-token/api_getaccesstoken)、[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken) |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| app\_id | string | 是 | 业务方appid |
| open\_id | string | 是 | 微信用户openid |
| wxmed\_authcode | string | 是 | 实名信息code，对应url中的wxmed\_authcode，有效期10分钟 |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | [错误码](#apierrcode) |
| errmsg | string | [错误信息](#apierrcode) |
| cipher\_real\_name | string | 加密后的实名信息，base64后的加密信息 |
| cipher\_algorithm | string | 加密算法，默认：AES\_256\_ECB\_PKCS7Padding |
| key\_version | number | 实名信息加密key版本号，初始版本号为0，用于识别后续密钥更换升级 |
| app\_id | string | 业务方appid |
| open\_id | string | 微信用户openid |

## [#](#_4-注意事项) 4. 注意事项

用户实名数据属于敏感信息，不能以明文形式传输，所以平台返回的实名信息是经过对称加密后的base64字符串，平台会给进驻的每家医院分配长度为32位(256bit)密钥，解密后可获得明文，默认使用的加解密算法为：AES\_256\_ECB\_PKCS7Padding；解密示例代码[下载](https://share.weiyun.com/HPYWwdQU)

**解密后的实名明文**

```
{"real_name":"张三","id_card_no":"45088100000000","id_card_type":1,"phone":"13800000138","timestamp":1661420431,"phone_country_code":"86"}
```

**实名信息字段说明**

| 字段 | 字段名 | 类型 | 是否必填 | 说明 |
| --- | --- | --- | --- | --- |
| real\_name | 姓名 | string | 是 |  |
| id\_card\_no | 证件号 | string | 是 |  |
| id\_card\_type | 证件类型 | int32 | 是 | 1 居民身份证； 4 澳门居民往来内地通行证； 5 台湾居民往来内地通行证； 6香港居民往来内地通行证。 |
| phone | 电话号码 | string | 是 |  |
| timestamp | 时间戳 | int64 | 是 |  |

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
  "app_id": "wx23dde3xd34569cba",
  "open_id": "ont-9vr_is4GBmeuh_xy1YHidhgY",
  "wxmed_authcode": "BMUewIb9qr2GMDeInZKOBg.."
}
```

返回示例

```
{
  "app_id":"",
  "openid_id":""
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| 0 | ok | ok |
| 11200 | wxmed\_authcode expired |  |

## [#](#_7-适用范围) 7. 适用范围

本接口暂未明确可调用账号类型，或在业务中根据调用传参自行确定是否可调用，请以实际调用情况为准。

Incorrect translation.