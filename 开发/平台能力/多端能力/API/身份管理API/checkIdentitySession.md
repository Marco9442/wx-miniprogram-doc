# [#](#wx-checkIdentitySession) wx.checkIdentitySession

检查系统登录态，在系统登录态生效期间，可通过调用<wx.getMiniProgramCode>、<wx.getIdentityCode> 静默获得登录凭证。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数 |

#### [#](#object-fail-回调函数) object.fail 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errCode | number | 错误码 |
| errMsg | string | 错误提示 |

**res.errCode**

| errCode | 说明 |
| --- | --- |
| -1 | system error |

## [#](#示例代码) 示例代码

```
wx.checkIdentitySession({
  success () {
      console.log('系统登录态生效')
  },
  fail (res) {
      console.log('系统登录态失效')
  }
})
```

Incorrect translation.