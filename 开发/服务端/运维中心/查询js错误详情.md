# [#](#查询js错误详情) 查询js错误详情

[调试诊断](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_tools)

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：getJsErrDetail

该接口用于查询JS错误详情

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/wxaapi/log/jserr_detail?access_token=ACCESS_TOKEN
```

> **支持加密请求：** 本接口支持服务通信二次加密和签名，可有效防止数据篡改与泄露。[查看详情](../../getting_started/api_signature)

### [#](#云调用) 云调用

- 调用方法：operation.getJsErrDetail
- 出入参和 HTTPS 调用相同，调用方式可查看 [云调用](https://developers.weixin.qq.com/doc/oplatform/developers/dev/cloudCall) 说明文档。

### [#](#第三方调用) 第三方调用

- 本接口支持第三方平台代商家调用。
- 该接口所属的权限集 id 为：18
- 服务商获得其中之一权限集授权后，可通过使用 [authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/Before_Develop/call_interface) 说明文档。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| access\_token | string | 是 | 接口调用凭证，可使用 [access\_token](../mp-access-token/api_getaccesstoken)、[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken) |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startTime | string | 是 | 开始时间， 格式 "xxxx-xx-xx" |
| endTime | string | 是 | 结束时间，格式 “xxxx-xx-xx” |
| errorMsgMd5 | string | 是 | 错误信息的md5 |
| errorStackMd5 | string | 是 | errorStack的Md5信息 |
| appVersion | string | 是 | 小程序版本 "0"代表全部， 例如：“2.0.18” |
| sdkVersion | string | 是 | 基础库版本 "0"表示所有版本，例如 "2.14.1" |
| osName | string | 是 | 系统类型 "0"【全部】，"1" 【安卓】，"2" 【IOS】，"3"【其他】 |
| clientVersion | string | 是 | 客户端版本 "0"表示所有版本， 例如 "7.0.22" |
| openid | string | 是 | 发生错误的用户 openId |
| offset | number | 是 | 分页起始值 |
| limit | number | 是 | 一次拉取最大值 |
| desc | string | 是 | 排序规则 "0" 升序, "1" 降序 |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | [错误码](#apierrcode) |
| errmsg | string | [错误信息](#apierrcode) |
| data | [objarray](#Res__data<Array>) | 错误列表 |
| totalCount | number | 总条数 |

### [#](#Res-data-Array-Object-Payload) Res.data(Array) `Object Payload`

错误列表

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| Count | string | 数量 |
| sdkVersion | string | sdkVersion |
| ClientVersion | string | ClientVersion |
| errorStackMd5 | string | errorStackMd5 |
| TimeStamp | string | 时间戳 |
| appVersion | string | appVersion |
| errorMsgMd5 | string | errorMsgMd5 |
| errorMsg | string | errorMsg |
| errorStack | string | errorStack |
| Ds | string | 日期 |
| OsName | string | OsName |
| openId | string | openId |
| pluginversion | string | pluginversion |
| appId | string | appId |
| DeviceModel | string | DeviceModel |
| source | string | source |
| route | string | route |
| nickname | string | 昵称 |

## [#](#_4-注意事项) 4. 注意事项

本接口无特殊注意事项

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
  "startTime": "2021-01-25",
  "endTime": "2021-01-26",
  "errorMsgMd5": "f2fb4f8cd638466ad0e7607b01b7d0ca",
  "errorStackMd5": "795a63b70ce5755c7103611d93077603",
  "appVersion": "0",
  "sdkVersion": "0",
  "osName": "2",
  "clientVersion": "0",
  "openid": "",
  "offset": 0,
  "limit": 10,
  "desc": "0"
}
```

返回示例

```
{
  "success": true,
  "openid": "",
  "data": [
    {
      "Count": "1",
      "sdkVersion": "2.14.1",
      "ClientVersion": "7.0.21",
      "errorStackMd5": "e371cd9cae821969c855f9f461327dac",
      "TimeStamp": "2021-01-25 16:36:39",
      "appVersion": "2.6.16",
      "errorMsgMd5": "53b4825ec4a41d966f88c298c718de80",
      "errorMsg": "errCode: -404012 polling exceed max timeout retry | errMsg: cloud.callFunction:fail polling exceed max timeout retry (callId: 1611553677669-0.2531087324274228) (trace: 13:47:57 start->13:48:12 timeout, retry->13:48:18 app hide->13:48:27 timeout, retry->13:48:42 timeout, abort); at cloud.callFunction api; ",
      "errorStack": "Error: errCode: -404012 polling exceed max timeout retry | errMsg: cloud.callFunction:fail polling exceed max timeout retry (callId: 1611553677669-0.2531087324274228) (trace: 13:47:57 start->13:48:12 timeout, retry->13:48:18 app hide->13:48:27 timeout, retry->13:48:42 timeout, abort); at cloud.callFunction api; \n    at new t (https://usr/app-service.js:2:320930)\n    at c (https://usr/app-service.js:2:321660)\n    at l (https://usr/app-service.js:2:321755)\n    at https://usr/app-service.js:2:297192\n    at https://usr/app-service.js:2:76398\n    at Object.next (https://usr/app-service.js:2:76503)\n    at s (https://usr/app-service.js:2:75234)",
      "Ds": "2021-01-25",
      "OsName": "1",
      "openId": "o-0YS0ZNM_bzkm13NKNUSwbrEkYU",
      "pluginversion": "0",
      "appId": "wxcff7381e631cf54e",
      "DeviceModel": "Redmi Note 5Aarm64-v8a",
      "source": "",
      "route": "",
      "Uin": "",
      "nickname": ""
    }
  ],
  "totalCount": 1,
  "errcode": 0
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| -3 | 系统繁忙 | 请稍后再试 |
| -1 | system error | 系统繁忙，此时请开发者稍候再试 |
| 40001 | invalid credential  access\_token isinvalid or not latest | 获取 access\_token 时 AppSecret 错误，或者 access\_token 无效。请开发者认真比对 AppSecret 的正确性，或查看是否正在为恰当的公众号调用接口 |

## [#](#_7-适用范围) 7. 适用范围

本接口在不同账号类型下的可调用情况：

| 小程序 | 小游戏 |
| --- | --- |
| ✔ | ✔ |

- ✔：该账号可调用此接口。
- 其他未明确声明的账号类型，如无特殊说明，均不可调用此接口。

Incorrect translation.