# [#](#Command-or-expressions-any-Command) [Command](../Command).or(expressions: any[]): [Command](../Command)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

查询操作符，用于表示逻辑 "或" 的关系，表示需同时满足多个查询筛选条件。或指令有两种用法，一是可以进行字段值的 “或” 操作，二是也可以进行跨字段的 “或” 操作。

## [#](#参数) 参数

### [#](#expressions-any) expressions: any[]

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#字段值的或操作) 字段值的或操作

字段值的 “或” 操作指的是指定一个字段值为多个值之一即可。

如筛选出进度大于 80 或小于 20 的 todo：

流式写法：

```
const _ = db.command
db.collection('todo').where({
  progress: _.gt(80).or(_.lt(20))
})
```

前置写法：

```
const _ = db.command
db.collection('todo').where({
  progress: _.or(_.gt(80), _.lt(20))
})
```

前置写法也可接收一个数组：

```
const _ = db.command
db.collection('todo').where({
  progress: _.or([_.gt(80), _.lt(20)])
})
```

## [#](#跨字段的或操作) 跨字段的或操作

跨字段的 “或” 操作指条件 “或”，相当于可以传入多个 where 语句，满足其中一个即可。

如筛选出进度大于 80 或已标为已完成的 todo：

```
const _ = db.command
db.collection('todo').where(_.or([
  {
    progress: _.gt(80)
  },
  {
    done: true
  }
]))
```

## [#](#调用风格) 调用风格

方法接收两种传参方式，一是传入一个数组参数，二是传入多个参数，效果一样。

```
// 传入数组
function or(expressions: Expression[]): Command
// 传入多参数
function or(...expressions: Expression[]): Command
```

Incorrect translation.