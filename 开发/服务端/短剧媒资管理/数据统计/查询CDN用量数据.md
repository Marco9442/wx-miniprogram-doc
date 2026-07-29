# [#](#查询CDN用量数据) 查询CDN用量数据

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：getCdnUsageData

该接口用于查询点播 CDN 的流量数据。

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/wxa/sec/vod/getcdnusagedata?access_token=ACCESS_TOKEN
```

### [#](#云调用) 云调用

- 本接口不支持云调用。

### [#](#第三方调用) 第三方调用

- 本接口支持第三方平台代商家调用。
- 该接口所属的权限集 id 为：153
- 服务商获得其中之一权限集授权后，可通过使用 [authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/Before_Develop/call_interface) 说明文档。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 示例 | 说明 |
| --- | --- | --- | --- | --- |
| access\_token | string | 是 | ACCESS\_TOKEN | 接口调用凭证，可使用 [access\_token](../../mp-access-token/api_getaccesstoken)、[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken) |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start\_time | number | 是 | 起始时间戳。 |
| end\_time | number | 是 | 截止时间戳。 |
| data\_interval | string | 是 | 用量数据的时间粒度，单位：分钟，取值有：5：5 分钟粒度，返回指定查询时间内5分钟粒度的明细数据。60：小时粒度，返回指定查询时间内1小时粒度的数据。1440：天粒度，返回指定查询时间内1天粒度的数据。默认值为1440，返回天粒度的数据。 |
| query\_type | number | 否 | 查询类型，0：通用播放流量和短剧播放器定向流量；1：短剧播放器定向流量；2：通用播放流量。默认值为0。 |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 示例 | 说明 |
| --- | --- | --- | --- |
| errcode | number | - | [错误码](#apierrcode) |
| errmsg | string | ok | [错误信息](#apierrcode) |
| data\_interval | number | - | 时间粒度，单位：分钟。 |
| item\_list | [objarray](#Res__item_list<Array>) | - | CDN 统计数据。 |

### [#](#Res-item-list-Array-Object-Payload) Res.item\_list(Array) `Object Payload`

CDN 统计数据。

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| time | number | 数据所在时间区间的开始时间戳。 |
| value | number | 数据大小，单位：字节。 |

## [#](#_4-注意事项) 4. 注意事项

1. 可以查询最近365天内的 CDN 用量数据。
2. 查询时间跨度不超过90天。
3. 可以指定用量数据的时间粒度，支持5分钟、1小时、1天的时间粒度。
4. 流量为查询时间粒度内的总流量。
5. 流量进制换算规则：1GB=1000MB、1MB=1000KB

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
    "start_time": 1682870400,
    "end_time": 1682956800,
    "data_interval": 5
}
```

返回示例

```
{
    "errcode": 0,
    "errmsg": "ok",
    "data_interval": 5,
    "item_list": [
        {
            "time": 1682870400,
            "value": 123
        },
        ...
    ]
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 |
| --- | --- |
| -2 | 初始化未完成，请稍后再试 |
| -1 | 系统错误 |
| 43002 | HTTP请求必须使用POST方法 |
| 44002 | POST内容为空 |
| 47001 | 输入格式错误 |
| 47003 | 参数不符合要求 |
| 10090001 | 视频类型不支持 |
| 10090002 | 图片类型不支持 |
| 10090003 | 图片URL无效 |
| 10090005 | resource\_type无效 |
| 10090038 | 被授权账号没有【文娱-微短剧】类目 |
| 10090039 | 已经被解除授权 |
| 10090040 | 剧集已经被占用 |
| 10090041 | 剧目名称不符合规范 |
| 10090042 | 剧集名称不符合规范 |
| 10090043 | 不存在授权关系 |
| 10093011 | 操作失败 |
| 10093014 | 参数错误（包括参数格式、类型等错误） |
| 10093023 | 操作过于频繁 |
| 10093030 | 资源不存在 |

## [#](#_7-适用范围) 7. 适用范围

本接口暂未明确可调用账号类型，或在业务中根据调用传参自行确定是否可调用，请以实际调用情况为准。

Incorrect translation.