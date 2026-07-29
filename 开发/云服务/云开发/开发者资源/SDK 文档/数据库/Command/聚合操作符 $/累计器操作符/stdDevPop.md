# [#](#AggregateCommand-stdDevPop-value-Expression-Object) <AggregateCommand>.stdDevPop(value: [Expression](../../aggregate/Expression)): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。返回一组字段对应值的标准差。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)

表达式

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`stdDevPop` 的使用形式如下：

```
db.command.aggregate.stdDevPop(<表达式>)
```

表达式传入的是指定字段，指定字段对应的值的数据类型必须是 `number` ，否则结果会返回 `null`。

## [#](#示例代码) 示例代码

假设集合 `students` 的记录如下：`a` 组同学的成绩分别是84和96，`b`组同学的成绩分别是80和100。

```
{ "group":"a", "score":84 }
{ "group":"a", "score":96 }
{ "group":"b", "score":80 }
{ "group":"b", "score":100 }
```

可以用 `stdDevPop` 来分别计算 `a` 和 `b` 两组同学成绩的标准差，以此来比较哪一组同学的成绩更稳定。代码如下：

```
const $ = db.command.aggregate
db.collection('students').aggregate()
  .group({
    _id: '$group',
    stdDev: $.stdDevPop('$score')
  })
  .end()
```

返回的数据结果如下：

```
{ "_id": "b", "stdDev": 10 }
{ "_id": "a", "stdDev": 6 }
```

Incorrect translation.