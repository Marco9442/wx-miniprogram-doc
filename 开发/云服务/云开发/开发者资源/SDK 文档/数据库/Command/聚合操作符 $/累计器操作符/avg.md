# [#](#AggregateCommand-avg-value-Expression-number-Object) <AggregateCommand>.avg(value: [Expression](../../aggregate/Expression)<number>): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。返回一组集合中，指定字段对应数据的平均值。

## [#](#参数) 参数

### [#](#value-Expression-number) value: [Expression](../../aggregate/Expression)<number>

number

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`avg` 的语法如下：

```
db.command.aggregate.avg(<number>)
```

`avg` 传入的值除了数字常量外，也可以是任何最终解析成一个数字的表达式。它会忽略非数字值。

## [#](#示例代码) 示例代码

假设集合 `students` 的记录如下：

```
{ "group": "a", "name": "stu1", "score": 84 }
{ "group": "a", "name": "stu2", "score": 96 }
{ "group": "b", "name": "stu3", "score": 80 }
{ "group": "b", "name": "stu4", "score": 100 }
```

借助 `avg` 可以计算所有记录的 `score` 的平均值：

```
const $ = db.command.aggregate
db
  .collection('students')
  .aggregate()
  .group({
    _id: null,
    average: $.avg('$score')
  })
  .end()
```

返回的结果如下：

```
{ "_id": null, "average": 90 }
```

Incorrect translation.