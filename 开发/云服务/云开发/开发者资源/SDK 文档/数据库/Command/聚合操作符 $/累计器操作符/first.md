# [#](#AggregateCommand-first-value-Expression-Object) <AggregateCommand>.first(value: [Expression](../../aggregate/Expression)): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。返回指定字段在一组集合的第一条记录对应的值。仅当这组集合是按照某种定义排序（ `sort` ）后，此操作才有意义。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)

表达式

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`first` 的语法如下：

```
db.command.aggregate.first(<表达式>)
```

表达式是形如 `$ + 指定字段` 的字符串。

`first` 只能在 `group` 阶段被使用，并且需要配合 `sort` 才有意义。

## [#](#示例代码) 示例代码

假设集合 `students` 的记录如下：

```
{ "group": "a", "name": "stu1", "score": 84 }
{ "group": "a", "name": "stu2", "score": 96 }
{ "group": "b", "name": "stu3", "score": 80 }
{ "group": "b", "name": "stu4", "score": 100 }
```

如果需要得到所有记录中 `score` 的最小值，可以先将所有记录按照 `score` 排序，然后取出第一条记录的 `first`。

```
const $ = db.command.aggregate
db
  .collection('students')
  .aggregate()
  .sort({
    score: 1
  })
  .group({
    _id: null,
    min: $.first('$score')
  })
  .end()
```

返回的数据结果如下：

```
{ "_id": null, "min": 80 }
```

Incorrect translation.