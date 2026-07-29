# [#](#Command-mod-divisor-number-remainder-number-Command) [Command](../Command).mod(divisor: number, remainder: number): [Command](../Command)

> 支持端：[小程序 2.8.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 1.2.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

查询筛选操作符，给定除数 divisor 和余数 remainder，要求字段作为被除数时 value % divisor = remainder。

## [#](#参数) 参数

### [#](#divisor-number) divisor: number

### [#](#remainder-number) remainder: number

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例代码) 示例代码

找出进度为 10 的倍数的字段的记录

```
const _ = db.command
db.collection('todos').where({
  progress: _.mod(10, 0)
})
.get({
  success: console.log,
  fail: console.error
})
```

Incorrect translation.