# [#](#获取ShortLink) 获取ShortLink

[调试诊断](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_tools)

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：generateShortLink

获取小程序 Short Link，适用于微信内拉起小程序的业务场景。目前对所有非个人主体小程序开放。通过该接口，可以选择生成到期失效和永久有效的小程序短链。

详情见[获取 Short Link](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/shortlink)。

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/wxa/genwxashortlink?access_token=ACCESS_TOKEN
```

### [#](#云调用) 云调用

- 调用方法：shortlink.generate
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
| page\_url | string | 是 | 通过 Short Link 进入的小程序页面路径，必须是已经发布的小程序存在的页面，可携带 query，最大1024个字符 |
| page\_title | string | 否 | 短链标题，可自定义，不能包含违法信息，超过20字符会用... 截断代替 |
| is\_permanent | boolean | 否 | 默认值false。生成的 Short Link 类型，短期有效：false，永久有效：true |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 | 枚举 |
| --- | --- | --- | --- |
| errcode | number | [错误码](#apierrcode) | [枚举值](#Enum_Res__errcode) |
| errmsg | string | [错误信息](#apierrcode) | - |
| link | string | 生成的小程序 Short Link | - |

## [#](#_4-枚举信息) 4. 枚举信息

### [#](#Res-errcode-Enum) Res.errcode `Enum`

[错误码](#apierrcode)

| 枚举值 | 描述 |
| --- | --- |
| 40001 | invalid credential access\_token isinvalid or not latest； 获取 access\_token 时 AppSecret 错误，或者 access\_token 无效。请开发者认真比对 AppSecret 的正确性，或查看是否正在为恰当的公众号调用接口 |
| 40066 | invalid url；url不存在，即，已发布小程序没有对应url |
| 40225 | invalid page title；无效的页面标题 |
| 85400 | reach max long time quota limit；长期有效Scheme或short link达到生成上限10万，不可再生成。 |
| 45009 | 单天生成Short Link数量超过上限1000万 |
| 43104 | this appid does not have permission；没有调用权限，参考api权限限制 |

## [#](#_5-注意事项) 5. 注意事项

#### [#](#调用上限) 调用上限

Link 将根据是否为到期有效与失效时间参数，分为 **短期有效ShortLink** 与 **永久有效ShortLink**：

- 单个小程序每日生成 ShortLink 上限为1000万个（包含短期有效 ShortLink 与长期有效 ShortLink ）
- 单个小程序总共可生成永久有效 ShortLink 上限为10万个，请谨慎调用。
- 短期有效ShortLink 有效时间为30天，单个小程序生成短期有效ShortLink 不设上限。

## [#](#_6-代码示例) 6. 代码示例

请求示例

```
{
    "page_url": "pages/publishHomework/publishHomework?query1=q1",
    "page_title": "Homework title",
    "is_permanent":false
}
```

返回示例

```
{
 "errcode": 0,
 "errmsg": "ok",
 "link": "Short Link"
}
```

## [#](#_7-错误码) 7. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| 40001 | invalid credential access\_token isinvalid or not latest | 获取 access\_token 时 AppSecret 错误，或者 access\_token 无效。请开发者认真比对 AppSecret 的正确性，或查看是否正在为恰当的公众号调用接口 |
| 40066 | invalid url | url不存在，即，已发布小程序没有对应url |
| 40225 | invalid page title | 无效的页面标题 |
| 43104 | this appid does not have permission | 没有调用权限，目前只开放给电商类目（具体包含以下一级类目：电商平台、商家自营、跨境电商） |
| 45009 | 单天生成Short Link数量超过上限1000万 |  |
| 85400 | reach max long time quota limit | 长期有效Scheme或short link达到生成上限10万，不可再生成。 |

## [#](#_8-适用范围) 8. 适用范围

本接口支持「小程序」账号类型调用。其他账号类型如无特殊说明，均不可调用。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/56617deb-b17d-4cf1-bccd-71d2c41ccc76.svg)接口变更日志（1条）

2026 年 02 月 03 日

更新 `page_title` 字段描述

Incorrect translation.