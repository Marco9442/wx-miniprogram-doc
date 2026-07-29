# [#](#查询license资源包列表) 查询license资源包列表

[调试诊断](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_tools)

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：getLicensePkgList

查询小程序已购买的 license 资源包列表信息。

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/wxa/business/license/getpkglist?access_token=ACCESS_TOKEN
```

### [#](#云调用) 云调用

- 本接口不支持云调用。

### [#](#第三方调用) 第三方调用

- 本接口支持第三方平台代商家调用。
- 该接口所属的权限集 id 为：118
- 服务商获得其中之一权限集授权后，可通过使用 [authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/Before_Develop/call_interface) 说明文档。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| access\_token | string | 是 | 接口调用凭证，可使用 [access\_token](../mp-access-token/api_getaccesstoken)、[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken) |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pkg\_type | number | 是 | 资源包类型，0：测试体验包，1：A 类设备，2：B 类设备，3：C 类设备，4：D 类设备，5：E类设备 |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | [错误码](#apierrcode) |
| errmsg | string | [错误信息](#apierrcode) |
| pkg\_list | [objarray](#Res__pkg_list<Array>) | 资源包列表 |
| max\_active\_number | number | 最大激活码序号，已废弃。 |

### [#](#Res-pkg-list-Array-Object-Payload) Res.pkg\_list(Array) `Object Payload`

资源包列表

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| pkg\_id | string | 资源包 ID |
| pkg\_type | number | 资源包类型 |
| start\_time | number | 资源包下单时间 |
| end\_time | number | 资源包过期时间 |
| pkg\_status | number | 资源包状态，1为已生效，2为未生效，3为已过期 |
| used | number | 已使用额度 |
| all | number | 资源包总量 |

## [#](#_4-注意事项) 4. 注意事项

开发者需要先在小程序管理后台购买设备 license 的套餐包后，方可查询到对应的资源包。

本接口将于2024年12月31日正式回收，请开发者及时进行调整适配。

详见[调整公告](https://developers.weixin.qq.com/community/minihome/doc/000428b5bd4d10c54812f7cd466401)

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
  "pkg_type": 0
}
```

返回示例

```
{
  "errcode": 0,
  "errmsg": "success",
  "pkg_list": [
    {
      "pkg_id": "ZY100000000",
      "pkg_type": 1,
      "start_time": 1629907200,
      "end_time": 1630425600,
      "pkg_status": 1,
      "used": 10,
      "all": 100
    },
    {
      "pkg_id": "ZY100000001",
      "pkg_type": 2,
      "start_time": 1629907200,
      "end_time": 1630425600,
      "pkg_status": 1,
      "used": 20,
      "all": 200
    }
  ],
  "max_active_number": 300
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| 0 | ok | ok |

## [#](#_7-适用范围) 7. 适用范围

本接口暂未明确可调用账号类型，或在业务中根据调用传参自行确定是否可调用，请以实际调用情况为准。

Incorrect translation.