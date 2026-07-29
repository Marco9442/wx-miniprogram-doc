# [#](#AggregateCommand-min-value-Expression-Object) <AggregateCommand>.min(value: [Expression](../../aggregate/Expression)): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。返回一组数值的最小值。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)

表达式

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`min` 的语法如下：

```
db.command.aggregate.min(<表达式>)
```

表达式是形如 `$ + 指定字段` 的字符串。

## [#](#示例代码) 示例代码

假设集合 `students` 的记录如下：

```
{ "group": "a", "name": "stu1", "score": 84 }
{ "group": "a", "name": "stu2", "score": 96 }
{ "group": "b", "name": "stu3", "score": 80 }
{ "group": "b", "name": "stu4", "score": 100 }
```

借助 `min` 可以统计不同组（ `group` ）中成绩的最低值，代码如下：

```
const $ = db.command.aggregate
db
  .collection('students')
  .aggregate()
  .group({
    _id: '$group',
    minScore: $.min('$score')
  })
  .end()
```

返回的数据结果如下：

```
{ "_id": "b", "minScore": 80 }
{ "_id": "a", "minScore": 84 }
```

Incorrect translation.