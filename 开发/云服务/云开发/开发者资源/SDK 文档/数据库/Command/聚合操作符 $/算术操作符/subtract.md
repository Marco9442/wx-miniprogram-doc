# [#](#AggregateCommand-subtract-value-Expression-Object) <AggregateCommand>.subtract(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。将两个数字相减然后返回差值，或将两个日期相减然后返回相差的毫秒数，或将一个日期减去一个数字返回结果的日期。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<expression1>, <expression2>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.subtract([<expression1>, <expression2>])
```

参数可以是任意解析为数字或日期的表达式。

## [#](#示例代码) 示例代码

假设集合 `scores` 有如下记录：

```
{ "_id": 1, "max": 10, "min": 1 }
{ "_id": 2, "max": 7, "min": 5 }
{ "_id": 3, "max": 6, "min": 6 }
```

求各个记录的 `max` 和 `min` 的差值。：

```
const $ = db.command.aggregate
db.collection('scores').aggregate()
  .project({
    diff: $.subtract(['$max', '$min'])
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "diff": 9 }
{ "_id": 2, "diff": 2 }
{ "_id": 3, "diff": 0 }
```

Incorrect translation.