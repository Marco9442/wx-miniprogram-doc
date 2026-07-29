# [#](#AggregateCommand-or-value-Expression-Object) <AggregateCommand>.or(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。给定多个表达式，如果任意一个表达式返回 `true`，则 `or` 返回 `true`，否则返回 `false`。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<expression1>, <expression2>, ...]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.or([<expression1>, <expression2>, ...])
```

如果表达式返回 `false`、`null`、`0`、或 `undefined`，表达式会解析为 `false`，否则对其他返回值都认为是 `true`。

## [#](#示例代码) 示例代码

假设集合 `price` 有如下记录：

```
{ "_id": 1, "min": 10, "max": 100 }
{ "_id": 2, "min": 60, "max": 80 }
{ "_id": 3, "min": 30, "max": 50 }
```

求 `min` 小于 40 或 `max` 大于 60 的记录。

```
const $ = db.command.aggregate
db.collection('price').aggregate()
  .project({
    fullfilled: $.or([$.lt(['$min', 30]), $.gt(['$max', 60])])
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "fullfilled": true }
{ "_id": 2, "fullfilled": false }
{ "_id": 3, "fullfilled": true }
```

Incorrect translation.