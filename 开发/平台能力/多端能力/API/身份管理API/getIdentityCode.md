# [#](#wx-getIdentityCode) wx.getIdentityCode

在系统登录态生效期间，可通过调用该接口获得登录凭证用于请求服务端 API [code2Verifyinfo](../../openapi/code2Verifyinfo)。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数 |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| code | string | 用户登录凭证（有效期五分钟）。开发者可以在开发者服务器调用 [code2Verifyinfo](../../openapi/code2Verifyinfo)，使用 code 换取用户标识信息等 |

#### [#](#object-fail-回调函数) object.fail 回调函数

##### [#](#参数-3) 参数

###### [#](#Object-res-2) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errCode | number | 错误码 |
| errMsg | string | 错误提示 |

**res.errCode**

| errCode | 说明 |
| --- | --- |
| -1 | system error |
| 10001011 | 系统登录态无效 |
| -700000 | 前端错误，errMsg 将给出详细提示 |

## [#](#示例代码) 示例代码

```
wx.getIdentityCode({
  success (res) {
      if (res.code) {
          console.log('临时登录凭证 code', res.code)
      }
  }
})
```

Incorrect translation.