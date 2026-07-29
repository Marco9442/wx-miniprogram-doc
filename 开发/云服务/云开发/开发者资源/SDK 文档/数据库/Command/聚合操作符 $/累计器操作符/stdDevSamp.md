# [#](#AggregateCommand-stdDevSamp-value-Expression-Object) <AggregateCommand>.stdDevSamp(value: [Expression](../../aggregate/Expression)): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。计算输入值的样本标准偏差。如果输入值代表数据总体，或者不概括更多的数据，请改用 `db.command.aggregate.stdDevPop`。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)

表达式

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`stdDevSamp` 的使用形式如下：

```
db.command.aggregate.stdDevSamp(<表达式>)
```

表达式传入的是指定字段，`stdDevSamp` 会自动忽略非数字值。如果指定字段所有的值均是非数字，那么结果返回 `null`。

## [#](#示例代码) 示例代码

假设集合 `students` 的记录如下：

```
{ "score": 80 }
{ "score": 100 }
```

可以用 `stdDevSamp` 来计算成绩的标准样本偏差。代码如下：

```
const $ = db.command.aggregate
db.collection('students').aggregate()
  .group({
    _id: null,
    ageStdDev: $.stdDevSamp('$score')
  })
  .end()
```

返回的数据结果如下：

```
{ "_id": null, "ageStdDev": 14.142135623730951 }
```

如果向集合 `students` 添加一条新记录，它的 `score` 字段类型是 `string`：

```
{ "score": "aa" }
```

用上面代码计算标准样本偏差时，`stdDevSamp` 会自动忽略类型不为 `number` 的记录，返回结果保持不变。

Incorrect translation.