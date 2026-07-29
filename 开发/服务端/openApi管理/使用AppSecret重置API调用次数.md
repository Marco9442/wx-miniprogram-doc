# [#](#使用AppSecret重置API调用次数) 使用AppSecret重置API调用次数

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：clearQuotaByAppSecret

本接口是通过AppSecret清空服务端接口的每日调用接口次数。

适用的账号类型为：公众号/服务号/小程序/小游戏/微信小店/带货助手/视频号助手/联盟带货机构/移动应用/网站应用/多端应用/第三方平台

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/cgi-bin/clear_quota/v2
```

### [#](#云调用) 云调用

- 本接口不支持云调用。

### [#](#第三方调用) 第三方调用

- 本接口不支持第三方平台调用。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

无

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appid | string | 是 | 要被清空的账号的appid |
| appsecret | string | 是 | 唯一凭证密钥，即 AppSecret |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | [错误码](#apierrcode) |
| errmsg | string | [错误信息](#apierrcode) |

## [#](#_4-注意事项) 4. 注意事项

1、该接口通过 appsecret 调用，解决了 accesss\_token 耗尽无法调用「重置 API 调用次数」的问题。

2、每个账号每月使用「重置 API 调用次数」与本接口共10次清零操作机会，清零生效一次即用掉一次机会；

3、由于指标计算方法或统计时间差异，实时调用量数据可能会出现误差，一般在1%以内

4、该接口仅支持POST调用

5、如果要清除 [获取令牌接口](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getcomponentaccesstoken) 调用次数或者以服务商身份代商家清除公众号或者小程序调用次数，则需要使用[使用AppSecret重置第三方平台API调用次数接口](https://developers.weixin.qq.com/doc/oplatform/openApi/openapi/api_componentclearquota_v2)。

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
POST  https://api.weixin.qq.com/cgi-bin/clear_quota/v2?appid=wx888888888888&appsecret=xxxxxxxxxxxxxxxxxxxxxxxx
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
| -1 | system error | 系统繁忙，此时请开发者稍候再试 |
| 40013 | invalid appid | 不合法的 AppID ，请开发者检查 AppID 的正确性，避免异常字符，注意大小写 |
| 41002 | appid missing | 缺少 appid 参数 |
| 41004 | appsecret missing | 缺少 secret 参数 |
| 48006 | forbid to clear quota because of reaching the limit | api 禁止清零调用次数，因为清零次数达到上限 |

## [#](#_7-适用范围) 7. 适用范围

本接口在不同账号类型下的可调用情况：

| 小程序 | 公众号 | 服务号 | 小游戏 | 微信小店 | 联盟带货机构 | 带货助手 | 小店供货商 | 移动应用 | 网站应用 | 视频号助手 | 多端应用 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |

- ✔：该账号可调用此接口。
- 其他未明确声明的账号类型，如无特殊说明，均不可调用此接口。

Incorrect translation.