# [#](#AggregateCommand-split-value-Expression-Object) <AggregateCommand>.split(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。按照分隔符分隔数组，并且删除分隔符，返回子字符串组成的数组。如果字符串无法找到分隔符进行分隔，返回原字符串作为数组的唯一元素。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<字符串表达式>, <分隔符表达式>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`split` 的语法如下：

```
db.command.aggregate.split([<字符串表达式>, <分隔符表达式>])
```

字符串表达式和分隔符表达式可以是任意形式的表达式，只要它可以被解析为字符串即可。

## [#](#示例代码) 示例代码

假设集合 `students` 的记录如下：

```
{ "birthday": "1999/12/12" }
{ "birthday": "1998/11/11" }
{ "birthday": "1997/10/10" }
```

通过 `split` 将每条记录中的 `birthday` 字段对应值分隔成数组，每个数组分别由代表年、月、日的3个元素组成：

```
const $ = db.command.aggregate
db
  .collection('students')
  .aggregate()
  .project({
    _id: 0,
    birthday: $.split(['$birthday', '/'])
  })
  .end()
```

返回的结果如下：

```
{ "birthday": [ "1999", "12", "12" ] }
{ "birthday": [ "1998", "11", "11" ] }
{ "birthday": [ "1997", "10", "10" ] }
```

Incorrect translation.