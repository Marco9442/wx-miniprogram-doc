# [#](#Command-unshift-values-any-Command) [Command](../Command).unshift(values: any[]): [Command](../Command)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

数组更新操作符，对一个值为数组的字段，往数组头部添加一个或多个值。或字段原为空，则创建该字段并设数组为传入值。

## [#](#参数) 参数

### [#](#values-any) values: any[]

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例代码) 示例代码

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    tags: _.unshift(['mini-program', 'cloud'])
  }
})
```

Incorrect translation.