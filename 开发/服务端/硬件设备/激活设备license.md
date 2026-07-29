# [#](#激活设备license) 激活设备license

[调试诊断](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_tools)

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：activeLicenseDevice

该接口用于批量绑定设备，并消耗相应的资源包中的激活码序号。

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/wxa/business/license/activedevice?access_token=ACCESS_TOKEN
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
| device\_list | [objarray](#Body__device_list<Array>) | 是 | 待激活的设备列表 |
| pkg\_type | number | 是 | 资源包类型，0：测试体验包（默认），1：A 类设备，2：B 类设备，3：C 类设备，4：D 类设备，5：E类设备 |

### [#](#Body-device-list-Array-Object-Payload) Body.device\_list(Array) `Object Payload`

待激活的设备列表

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| model\_id | string | 是 | 设备型号 id。通过微信公众平台注册设备获得。 |
| sn | string | 是 | 设备唯一序列号。由厂商分配。 |
| active\_number | number | 是 | 激活码序号，任意 uint32 整数（需与之前使用过的不重复）。主要用于防止重复请求导致重复激活。 |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | [错误码](#apierrcode) |
| errmsg | string | [错误信息](#apierrcode) |
| device\_list | [objarray](#Res__device_list<Array>) | 设备列表 |

### [#](#Res-device-list-Array-Object-Payload) Res.device\_list(Array) `Object Payload`

设备列表

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| model\_id | string | 设备型号唯一标识 |
| sn | string | 设备的唯一标识 |
| expire\_time | number | 设备的过期时间 |
| errcode | number | 错误码 |

## [#](#_4-注意事项) 4. 注意事项

- 正式license的使用：每次调用最多激活100个设备，且所有设备类型必须属于同一个资源包类型。每个激活码序号只能用于激活一台设备。每个设备最多绑定 3 个激活码序号，即剩余有效时间不能超过 3 年。
- 体验license的使用：详见[平台公告](https://developers.weixin.qq.com/community/minihome/doc/000204860703984b45c02830963c01)

## [#](#其他说明) 其他说明

1. 自2024年9月9日15时起，激活操作不再消耗license。为确保兼容性，本接口对于请求激活设备将返回无实际意义的「激活成功」，形如：

```
{
  "model_id": "MODEL_ID1",
  "sn": "SN1",
  "errcode": 0,
  "expire_time": 1893427200,
}
```

其中`errcode`固定返回0，`expire_time`固定返回`2030-01-01 00:00:00`时间戳

2. 本接口将于2024年12月31日正式回收，请开发者及时进行调整适配。

详见[调整公告](https://developers.weixin.qq.com/community/minihome/doc/000428b5bd4d10c54812f7cd466401)

## [#](#_5-代码示例) 5. 代码示例

请求示例

```
{
  "pkg_type": 0,
  "device_list": [
    {
      "model_id": "MODEL_ID1",
      "sn": "SN1",
      "active_number": 1
    },
    {
      "model_id": "MODEL_ID2",
      "sn": "SN2",
      "active_number": 2
    }
  ]
}
```

返回示例

```
{
  "errcode": 0,
  "errmsg": "ok",
  "device_list": [
    {
      "model_id": "MODEL_ID1",
      "sn": "SN1",
      "errcode": 0
    },
    {
      "model_id": "MODEL_ID2",
      "sn": "SN2",
      "errcode": 0
    }
  ]
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| 0 | ok | ok |
| 9800020 | 设备数超出限制 | 检查设备数量 |
| 9800020 | 设备数超出限制 | 检查设备数量 |
| 9800037 | 激活码序号已使用 | 更换激活码序号 |
| 9800038 | 设备有效期超出限制 | 检查设备有效期 |
| 9800039 | 资源包余额不足 | 检查资源包余额 |
| 9800040 | 资源包类型和设备类型不匹配 | 检查设备类型 |

## [#](#_7-适用范围) 7. 适用范围

本接口暂未明确可调用账号类型，或在业务中根据调用传参自行确定是否可调用，请以实际调用情况为准。

Incorrect translation.