# [#](#AggregateCommand-range-value-Expression-Object) <AggregateCommand>.range(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。返回一组生成的序列数字。给定开始值、结束值、非零的步长，`range` 会返回从开始值开始逐步增长、步长为给定步长、但不包括结束值的序列。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<start>, <end>, <non-zero step>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.range([<start>, <end>, <non-zero step>])
```

| 字段 | 说明 |
| --- | --- |
| start | 开始值，一个可以解析为整形的表达式 |
| end | 结束值，一个可以解析为整形的表达式 |
| non-zero step | 可选，步长，一个可以解析为非零整形的表达式，默认为 1 |

## [#](#示例代码) 示例代码

假设集合 `stats` 有如下记录：

```
{ "_id": 1, "max": 52 }
{ "_id": 2, "max": 38 }
```

```
const $ = db.command.aggregate
db.collection('stats').aggregate()
  .project({
    points: $.range([0, '$max', 10])
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "points": [0, 10, 20, 30, 40, 50] }
{ "_id": 2, "points": [0, 10, 20] }
```

Incorrect translation.