# [#](#查询CDN日志下载链接列表) 查询CDN日志下载链接列表

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：getCdnLogs

查询域名的 CDN 访问日志的下载链接。

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/wxa/sec/vod/getcdnlogs?access_token=ACCESS_TOKEN
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
| end\_time | number | 是 | 结束时间戳，必须大于起始时间，起始到结束时间的跨度不要超过48小时（end\_time-start\_time<=48h） |
| ‌~~limit~~ | number | 否 | 2024年3月29日起废弃。‌~~分页拉取的最大返回结果数。默认值：100；最大值：1000~~ |
| ‌~~offset~~ | number | 否 | 2024年3月29日起废弃。‌~~分页拉取的起始偏移量。默认值：0~~ |
| query\_type | number | 否 | 查询类型，0：通用播放流量和短剧播放器定向流量；1：短剧播放器定向流量；2：通用播放流量。默认值为0。 |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 示例 | 说明 |
| --- | --- | --- | --- |
| errcode | number | - | [错误码](#apierrcode) |
| errmsg | string | ok | [错误信息](#apierrcode) |
| total\_count | number | - | 日志下载链接总数量。 |
| domestic\_cdn\_logs | [object](#Res__domestic_cdn_logs) | - | 国内CDN节点的日志下载列表。 |

### [#](#Res-domestic-cdn-logs-Object-Payload) Res.domestic\_cdn\_logs `Object Payload`

国内CDN节点的日志下载列表。

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| date | number | 日志所属日期。 |
| name | number | 日志名称。 |
| url | number | 日志下载链接，24小时内下载有效。 |
| start\_time | number | 日志起始时间。 |
| end\_time | number | 日志结束时间 |

## [#](#_4-注意事项) 4. 注意事项

1. 可以查询最近30天内的 CDN 日志下载链接，单次查询的时间跨度不超过48小时。
2. 日志文件以小时为单位产生，但一个小时内可能会产生多个文件，每个文件对应一个域名，平台有可能使用多个域名分发。若某一个小时没有CDN访问，不会生成日志文件。
3. CDN 日志下载链接的有效期为24小时。
4. 日志字段依次为：请求时间、客户端 IP、访问域名、文件路径、字节数、省级编码、运营商编码、 HTTP 状态码、referer、Request-Time、 UA、range、HTTP Method、协议标识、缓存 HIT / MISS， 日志数据打包存在延迟，正常情况下3小时后数据包趋于完整日志中的字节数为应用层数据大小，未考虑网络协议包头、加速重传等开销，因此与计费数据存在一定差异。
5. CDN日志中记录的下行字节数统计而来的流量数据，是应用层数据。在实际网络传输中，产生的网络流量要比纯应用层流量多5%-15%，比如TCP/IP协议的包头消耗、网络丢包重传等，这些无法被应用层统计到。在业内标准中，计费用流量一般在应用层流量的基础上加上上述开销，媒资管理服务中计费的加速流量约为日志计算加速流量的110%。

#### [#](#省份映射) 省份映射

22：北京；86：内蒙古；146：山西；1069：河北；1177：天津；119：宁夏；152：陕西；1208：甘肃；1467：青海；1468：新疆；145：黑龙江；1445：吉林；1464：辽宁；2：福建；120：江苏；121：安徽；122：山东；1050：上海；1442：浙江；182：河南；1135：湖北；1465：江西；1466：湖南；118：贵州；153：云南；1051：重庆；1068：四川；1155：西藏；4：广东；173：广西；1441：海南；0：其他；1：港澳台；-1：海外。

#### [#](#运营商映射) 运营商映射

2：中国电信；26：中国联通；38：教育网；43：长城宽带；1046：中国移动；3947：中国铁通；-1：海外运营商；0：其他运营商。

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
    "start_time": 1711589350,
    "end_time": 1711632520,
}
```

返回示例

```
{
    "domestic_cdn_logs": [
        {
            "date": "2024-03-28",
            "end_time": 1711627199,
            "name": "2024032819-1500020822.vod2.myqcloud.com-mainland",
            "start_time": 1711623600,
            "url": "https://log-download.cdn.qcloud.com/20240328/19/2024032819-1500020822.vod2.myqcloud.com.gz?st=WdyksvfNz23NWKgEvcLQ&e=1711715411"
        },
        {
            "date": "2024-03-28",
            "end_time": 1711623599,
            "name": "2024032818-1500020822.vod2.myqcloud.com-mainland",
            "start_time": 1711620000,
            "url": "https://log-download.cdn.qcloud.com/20240328/18/2024032818-1500020822.vod2.myqcloud.com.gz?st=QmphynCTcO1G23-Ol-SlAg&e=1711715411"
        }
    ],
    "errcode": 0,
    "errmsg": "ok",
    "total_count": 2
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