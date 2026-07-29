# [#](#获取NFC的小程序scheme) 获取NFC的小程序scheme

[调试诊断](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_tools)

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：generateNFCScheme

该接口用于获取用于 NFC 的小程序 scheme 码，适用于 NFC 拉起小程序的业务场景。目前仅针对国内非个人主体的小程序开放，详见 [NFC 标签打开小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/NFC)。

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/wxa/generatenfcscheme?access_token=ACCESS_TOKEN
```

### [#](#云调用) 云调用

- 调用方法：urlscheme.generateNFCScheme
- 出入参和 HTTPS 调用相同，调用方式可查看 [云调用](https://developers.weixin.qq.com/doc/oplatform/developers/dev/cloudCall) 说明文档。

### [#](#第三方调用) 第三方调用

- 本接口不支持第三方平台调用。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| access\_token | string | 是 | 接口调用凭证，可使用 [access\_token](../../mp-access-token/api_getaccesstoken) |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jump\_wxa | [object](#Body__jump_wxa) | 否 | 跳转到的目标小程序信息。 |
| model\_id | string | 是 | scheme对应的设备model\_id |
| sn | string | 否 | scheme对应的设备sn，仅一机一码时填写 |

### [#](#Body-jump-wxa-Object-Payload) Body.jump\_wxa `Object Payload`

跳转到的目标小程序信息。

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 否 | 通过 scheme 码进入的小程序页面路径，必须是已经发布的小程序存在的页面，不可携带 query。path 为空时会跳转小程序主页 |
| query | string | 否 | 通过 scheme 码进入小程序时的 query，最大1024个字符，只支持数字，大小写英文以及部分特殊字符：`!#$&'()\*+,/:;=?@-.\_~%`` |
| env\_version | string | 否 | 要打开的小程序版本。正式版为"release"，体验版为"trial"，开发版为"develop"，仅在微信外打开时生效 |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | [错误码](#apierrcode) |
| errmsg | string | [错误信息](#apierrcode) |
| openlink | string | 生成的小程序 scheme 码 |

## [#](#_4-注意事项) 4. 注意事项

# [#](#调试) 调试

通过开发者工具的”快速 URL Schema编译“可以调试生成的 URL Schema

![](https://res8.wxqcloud.qq.com.cn/wxdoc/1f0b0493-b5d5-4fe9-8987-2a0c5abea3e2.png)

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
  "jump_wxa": {
    "path": "/pages/publishHomework/publishHomework",
    "query": ""
  },
  "sn": "xxx",
  "model_id": "xxx"
}
```

返回示例

```
{
 "errcode": 0,
 "errmsg": "ok",
 "openlink": Scheme
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| 40002 | 暂无生成权限（非个人主体小程序无权限，未申请 NFC 能力的小程序无权限） |  |
| 40013 | 生成权限被封禁 |  |
| 40165 | invalid weapp pagepath | 参数path填写错误，更正后重试 |
| 40212 | invalid query | 参数query填写错误 ，query格式遵循URL标准，即k1=v1&k2=v2 |
| 44990 | reach max api second frequence limit | 频率过快，超过100次/秒；降低调用频率 |
| 44993 | reach max api day frequence limit | 单天生成Scheme+URL Link数量超过上限50万 |
| 85079 | miniprogram has no online release | 小程序没有线上版本，即小程序尚未发布，不可进行该操作 |
| 85402 | invalid env\_version | 参数env\_version填写错误，更正后重试 |
| 9800003 | model\_id检查不通过 |  |
| 9800007 | 此model\_id尚未获得该能力，请能力申请通过后再试 |  |
| 9800008 | 能力类型为一机一码，sn不能为空 |  |
| 9800009 | 能力类型为一型一码，sn需为空 |  |

## [#](#_7-适用范围) 7. 适用范围

本接口暂未明确可调用账号类型，或在业务中根据调用传参自行确定是否可调用，请以实际调用情况为准。

Incorrect translation.