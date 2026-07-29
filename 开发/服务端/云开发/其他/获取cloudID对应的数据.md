# [#](#获取cloudID对应的数据) 获取cloudID对应的数据

[调试诊断](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_tools)

> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考[接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。

接口英文名：getOpenData

该接口用于换取 cloudID 对应的开放数据

## [#](#_1-调用方式) 1. 调用方式

### [#](#HTTPS-调用) HTTPS 调用

```
POST https://api.weixin.qq.com/wxa/getopendata?access_token=ACCESS_TOKEN&openid=OPENID
```

### [#](#云调用) 云调用

- 调用方法：cloudbase.getOpenData
- 出入参和 HTTPS 调用相同，调用方式可查看 [云调用](https://developers.weixin.qq.com/doc/oplatform/developers/dev/cloudCall) 说明文档。

### [#](#第三方调用) 第三方调用

- 本接口支持第三方平台代商家调用。
- 该接口所属的权限集 id 为：18、49
- 服务商获得其中之一权限集授权后，可通过使用 [authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/Before_Develop/call_interface) 说明文档。

## [#](#_2-请求参数) 2. 请求参数

### [#](#查询参数-Query-String-Parameters) 查询参数 `Query String Parameters`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| access\_token | string | 是 | 接口调用凭证，可使用 [access\_token](../../mp-access-token/api_getaccesstoken)、[authorizer\_access\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api_getauthorizeraccesstoken) |
| openid | string | 否 | 用户openid（敏感信息需要传入） |

### [#](#请求体-Request-Payload) 请求体 `Request Payload`

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cloudid\_list | array | 是 | CloudID 列表 |

## [#](#_3-返回参数) 3. 返回参数

### [#](#返回体-Response-Payload) 返回体 `Response Payload`

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | [错误码](#apierrcode) |
| errmsg | string | [错误信息](#apierrcode) |
| data\_list | [objarray](#Res__data_list<Array>) | 开放数据列表 |

### [#](#Res-data-list-Array-Object-Payload) Res.data\_list(Array) `Object Payload`

开放数据列表

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| cloud\_id | string | cloud id |
| json | string | 数据详情 |

## [#](#_4-注意事项) 4. 注意事项

本接口无特殊注意事项

## [#](#_5-代码示例) 5. 代码示例

### [#](#_5-1-HTTPS调用) 5.1 HTTPS调用

请求示例

```
// POST https://api.weixin.qq.com/wxa/getopendata?openid=OPENID&access_token=TOKEN
// url中支持传openid
{
 "cloudid_list": ["xxx"]
}
```

返回示例

```
{
  "errcode": 0,
  "errmsg": "ok",
  "data_list": [
    {
      "cloud_id": "xxx",
      "json": {
        "cloudID": "xxx",
        "data": {
          "stepInfoList": [
            {
              "timestamp": 1603641600,
              "step": 1234
            }
          ]
        }
      }
    }
  ]
}
```

### [#](#_5-2-云函数调用) 5.2 云函数调用

请求示例

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV,
})
exports.main = async (event, context) => {
  try {
    const result = await cloud.openapi.cloudbase.getOpenData({
        "cloudidList": [
          "xxx"
        ]
      })
    return result
  } catch (err) {
    return err
  }
}
```

返回示例

```
{
  "errCode": 0,
  "errMsg": "openapi.cloudbase.getOpenData:ok",
  "dataList": [
    {
      "json": {
        "cloudID": "xxx",
        "data": {
          "stepInfoList": [
            {
              "timestamp": 1603641600,
              "step": 1234
            }
          ]
        }
      },
      "cloudId": "xxx"
    }
  ]
}
```

## [#](#_6-错误码) 6. 错误码

以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm_source=api_errcode) 辅助定位和分析问题。

| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| -1 | system error | 系统繁忙，此时请开发者稍候再试 |

## [#](#_7-适用范围) 7. 适用范围

本接口在不同账号类型下的可调用情况：

| 小程序 | 公众号 | 服务号 | 小游戏 |
| --- | --- | --- | --- |
| ✔ | ✔ | ✔ | ✔ |

- ✔：该账号可调用此接口。
- 其他未明确声明的账号类型，如无特殊说明，均不可调用此接口。

Incorrect translation.