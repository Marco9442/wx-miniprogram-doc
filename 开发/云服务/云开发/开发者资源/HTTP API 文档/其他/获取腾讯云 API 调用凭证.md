# [#](#getQcloudToken) getQcloudToken

> 本接口应在服务器端调用，详细说明参见[服务端API](https://developers.weixin.qq.com/miniprogram/dev/server/getting_started/api_signature)。

获取腾讯云API调用凭证。[腾讯云可用 API 概览](https://cloud.tencent.com/document/api/876/34809)

### [#](#请求地址) 请求地址

```
POST https://api.weixin.qq.com/tcb/getqcloudtoken?access_token=ACCESS_TOKEN
```

### [#](#请求参数) 请求参数

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| access\_token / cloudbase\_access\_token | string |  | 是 | [接口调用凭证](../functions/invokeCloudFunction) |
| lifespan | number |  | 是 | 有效期（单位为秒，最大7200） |

### [#](#返回值) 返回值

### [#](#Object) Object

返回的 JSON 数据包

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | 错误码 |
| errmsg | string | 错误信息 |
| secretid | string | secretid |
| secretkey | string | secretkey |
| token | string | token |
| expired\_time | number | 过期时间戳 |

**errcode 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| 0 | 请求成功 |  |
| -1 | 系统错误 |  |
| -1000 | 系统错误 |  |
| 40014 | AccessToken 不合法 |  |
| 40097 | 请求参数错误 |  |
| 40101 | 缺少必填参数 |  |
| 41001 | 缺少AccessToken |  |
| 42001 | AccessToken过期 |  |
| 43002 | HTTP METHOD 错误 |  |
| 44002 | POST BODY 为空 |  |
| 45009 | 频率限制，一小时后再试 |  |
| 47001 | POST BODY 格式错误 |  |
| 85088 | 该APP未开通云开发 |  |
| 其他错误码 | [云开发错误码](../../reference/errcode) |  |

### [#](#频率限制) 频率限制

该接口有频率限制: 10次每小时。

### [#](#请求数据示例) 请求数据示例

```
{
  "lifespan" : 7200
}
```

### [#](#返回数据示例) 返回数据示例

```
{
    "errcode": 0,
    "errmsg": "ok",
    "secretid": "SECRETID",
    "secretkey": "SECRETKEY",
    "token": "TOKEN",
    "expired_time": 1557310488
}
```

腾讯云 API 调用说明

1. 本 API 换取的凭证只能用于[腾讯云可用API概览](https://cloud.tencent.com/document/api/876/34809)中所列API。
2. 调用凭证的使用参考[腾讯云公共参数](https://cloud.tencent.com/document/api/876/34812)

Incorrect translation.