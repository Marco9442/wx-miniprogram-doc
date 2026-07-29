# [#](#AggregateCommand-push-value-any-Object) <AggregateCommand>.push(value: any): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。在 `group` 阶段，返回一组中表达式指定列与对应的值，一起组成的数组。

## [#](#参数) 参数

### [#](#value-any) value: any

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`push` 语法如下：

```
db.command.aggregate.push({
  <字段名1>: <指定字段1>,
  <字段名2>: <指定字段2>,
  ...
})
```

## [#](#示例代码) 示例代码

假设集合 `students` 的记录如下：

```
{ "group": "a", "name": "stu1", "score": 84 }
{ "group": "a", "name": "stu2", "score": 96 }
{ "group": "b", "name": "stu3", "score": 80 }
{ "group": "b", "name": "stu4", "score": 100 }
```

借助 `push` 操作，对不同分组( `group` )的所有记录，聚合所有数据并且将其放入一个新的字段中，进一步结构化和语义化数据。

```
const $ = db.command.aggregate
db
  .collection('students')
  .aggregate()
  .group({
    _id: '$group',
    students: $.push({
      name: '$name',
      score: '$score'
    })
  })
  .end()
```

输出结果如下：

```
{ "_id": "b", "students": [{ "name": "stu3", "score": 80 }, { "name": "stu4", "score": 100 }] }
{ "_id": "a", "students": [{ "name": "stu1", "score": 84 }, { "name": "stu2", "score": 96 }] }
```

Incorrect translation.