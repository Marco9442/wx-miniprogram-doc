# [#](#Command-gt-value-any-Command) [Command](../Command).gt(value: any): [Command](../Command)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

查询筛选操作符，表示需大于指定值。可以传入 `Date` 对象用于进行日期比较。

## [#](#参数) 参数

### [#](#value-any) value: any

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例代码) 示例代码

找出进度大于 50 的 todo

```
const _ = db.command
db.collection('todos').where({
  progress: _.gt(50)
})
.get({
  success: console.log,
  fail: console.error
})
```

Incorrect translation.