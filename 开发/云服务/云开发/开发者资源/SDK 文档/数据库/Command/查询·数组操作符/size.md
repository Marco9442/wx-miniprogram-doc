# [#](#Command-size-value-string-Command) [Command](../Command).size(value: string): [Command](../Command)

> 支持端：[小程序 2.8.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 1.2.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

更新操作符，用于数组字段的查询筛选条件，要求数组长度为给定值

## [#](#参数) 参数

### [#](#value-string) value: string

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例) 示例

找出 tags 数组字段长度为 2 的所有记录

```
const _ = db.command
db.collection('todos').where({
  places: _.size(2)
})
.get({
  success: console.log,
  fail: console.error,
})
```

Incorrect translation.