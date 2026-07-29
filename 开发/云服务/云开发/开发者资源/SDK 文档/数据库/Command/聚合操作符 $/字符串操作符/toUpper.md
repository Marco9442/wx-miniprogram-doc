# [#](#AggregateCommand-toUpper-value-any-Object) <AggregateCommand>.toUpper(value: any): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。将字符串转化为大写并返回。

## [#](#参数) 参数

### [#](#value-any) value: any

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`toUpper` 的语法如下：

```
db.command.aggregate.toUpper(表达式)
```

只要表达式可以被解析成字符串，那么它就是有效表达式。例如：`$ + 指定字段`。

## [#](#示例代码) 示例代码

假设集合 `students` 的记录如下：

```
{ "firstName": "Yuanxin", "group": "a", "lastName": "Dong", "score": 84 }
{ "firstName": "Weijia", "group": "a", "lastName": "Wang", "score": 96 }
{ "firstName": "Chengxi", "group": "b", "lastName": "Li", "score": 80 }
```

借助 `toUpper` 将 `lastName` 的字段值转化为大写：

```
const $ = db.command.aggregate
db
  .collection('students')
  .aggregate()
  .project({
    _id: 0,
    result: $.toUpper('$lastName'),
  })
  .end()
```

返回的结果如下：

```
{ "result": "DONG" }
{ "result": "WANG" }
{ "result": "LI" }
```

Incorrect translation.