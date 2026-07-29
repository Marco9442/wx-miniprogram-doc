# [#](#Command-nin-value-any-Command) [Command](../Command).nin(value: any[]): [Command](../Command)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

查询筛选操作符，表示要求值不在给定的数组内。

## [#](#参数) 参数

### [#](#value-any) value: any[]

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例代码) 示例代码

找出进度不是 0 或 100 的 todo

```
const _ = db.command
db.collection('todos').where({
  progress: _.nin([0, 100])
})
.get({
  success: console.log,
  fail: console.error
})
```

Incorrect translation.