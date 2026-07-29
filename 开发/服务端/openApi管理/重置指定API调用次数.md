# [#](#重置指定API调用次数) 重置指定API调用次数

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：clearApiQuota

本接口使用 access\_token 来重置指定接口的每日调用次数

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/cgi-bin/openapi/quota/clear?access_token=ACCESS_TOKEN
```

### [#](#云调用) 云调用

- 本接口不支持云调用。

### [#](#第三方调用) 第三方调用

- 本接口支持第三方平台使用 [component\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/ComponentAccessToken) 自己调用，同时还支持代商家调用。
- 服务商获得任意权限集授权后，即可通过使用 [authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/Before_Develop/call_interface) 说明文档。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| access\_token | string | 是 | ACCESS\_TOKEN | 接口调用凭证，可使用 [access\_token](../mp-access-token/api_getaccesstoken)、[component\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getcomponentaccesstoken)、[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken) |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| cgi\_path | string | 是 | /channels/ec/basics/info/get | api的请求地址，cgi\_path 必须以"/channels/ec/"开头，不要前缀"https://api.weixin.qq.com"，也不要漏了"/" |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 示例 | 说明 |
| --- | --- | --- | --- |
| errcode | number | 0 | [错误码](#apierrcode) |
| errmsg | string | ok | [错误信息](#apierrcode) |

## [#](#_4-注意事项) 4. 注意事项

- 可用于重置小程序、公众号、微信小店等微信开发生态业务接口，cgi\_path 必须以"/"开头，例如"/channels/ec/"
- 如果是第三方服务商代清除quota，则需要用[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken)；
- 每个账号每月共50次清零操作机会，清零生效一次即用掉一次机会；
- 由于指标计算方法或统计时间差异，实时调用量数据可能会出现误差，一般在1%以内。

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
  "cgi_path":"/channels/ec/basics/info/get"
}
```

返回示例

```
{
  "errcode": 0,
  "errmsg": "ok"
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| 40001 | invalid credential  access\_token isinvalid or not latest | access\_token 无效或不为最新获取的 access\_token，请开发者确认access\_token的有效性 |
| 41001 | access\_token missing | 缺少 access\_token 参数 |
| 42001 | access\_token expired | access\_token 超时，请检查 access\_token 的有效期，请参考基础支持 - 获取 access\_token 中，对 access\_token 的详细机制说明 |
| 44002 | empty post data | POST 的数据包为空。post请求body参数不能为空。 |
| 45009 | reach max api daily quota limit | 超出接口每日调用限制 |
| 50002 | user limited | 用户受限，可能是用户帐号被冻结或注销 |
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