# [#](#Command-inc-value-number-Command) [Command](../Command).inc(value: number): [Command](../Command)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

更新操作符，原子操作，用于指示字段自增

## [#](#参数) 参数

### [#](#value-number) value: number

自增量，可正可负

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#原子自增) 原子自增

多个用户同时写，对数据库来说都是将字段自增，不会有后来者覆写前者的情况

## [#](#示例代码) 示例代码

将一个 todo 的进度自增 10：

```
const _ = db.command
db.collection('todos').doc('todo-id').update({
  data: {
    progress: _.inc(10)
  }
})
```

Incorrect translation.