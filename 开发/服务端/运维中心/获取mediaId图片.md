# [#](#获取mediaId图片) 获取mediaId图片

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：getFeedbackmedia

该接口用于获取 mediaId 图片

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
GET https://api.weixin.qq.com/cgi-bin/media/getfeedbackmedia?access_token=ACCESS_TOKEN&record_id=RECORD_ID&media_id=MEDIA_ID
```

### [#](#云调用) 云调用

- 调用方法：operation.getFeedbackmedia
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
| record\_id | number | 是 | 用户反馈信息的 record\_id, 可通过 [getFeedback](api_getfeedback) 获取 |
| media\_id | string | 是 | 图片的 mediaId |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

无

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | 错误码。如果成功，则直接返回图片实体，不返回errcode |
| errmsg | string | 错误信息。如果成功，则直接返回图片实体，不返回errsmg |

## [#](#_4-注意事项) 4. 注意事项

本接口无特殊注意事项

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
https://api.weixin.qq.com/cgi-bin/media/getfeedbackmedia?access_token=ACCESS_TOKEN&record_id=xxx&media_id=xx
```

返回示例

```
返回图片实体
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| -1 | system error | 系统繁忙，此时请开发者稍候再试 |
| 46001 | 不存在 mediaid 对应的数据 | 开发者自查 mediaid 是否正确 |

## [#](#_7-适用范围) 7. 适用范围

本接口在不同账号类型下的可调用情况：

| 小程序 | 小游戏 |
| --- | --- |
| ✔ | ✔ |

- ✔：该账号可调用此接口。
- 其他未明确声明的账号类型，如无特殊说明，均不可调用此接口。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/56617deb-b17d-4cf1-bccd-71d2c41ccc76.svg)接口变更日志（1条）

2026 年 03 月 17 日

返回码优化

Incorrect translation.