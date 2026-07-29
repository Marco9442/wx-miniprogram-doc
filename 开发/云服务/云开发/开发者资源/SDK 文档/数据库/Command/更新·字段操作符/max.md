# [#](#Command-max-value-any-Command) [Command](../Command).max(value: any): [Command](../Command)

> 支持端：[小程序 2.8.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 1.2.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

更新操作符，给定一个值，只有该值大于字段当前值才进行更新。

## [#](#参数) 参数

### [#](#value-any) value: any

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例代码) 示例代码

如果字段 progress < 50，则更新到 50

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    progress: _.max(50)
  }
})
```

Incorrect translation.