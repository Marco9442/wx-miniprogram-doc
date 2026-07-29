# [#](#AggregateCommand-not-value-Expression-Object) <AggregateCommand>.not(value: [Expression](../../aggregate/Expression)): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。给定一个表达式，如果表达式返回 `true`，则 `not` 返回 `false`，否则返回 `true`。注意表达式不能为逻辑表达式（`and`、`or`、`nor`、`not`）。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)

表达式

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.not(<expression>)
```

如果表达式返回 `false`、`null`、`0`、或 `undefined`，表达式会解析为 `false`，否则对其他返回值都认为是 `true`。

## [#](#示例代码) 示例代码

假设集合 `price` 有如下记录：

```
{ "_id": 1, "min": 10, "max": 100 }
{ "_id": 2, "min": 60, "max": 80 }
{ "_id": 3, "min": 30, "max": 50 }
```

求 `min` 不大于 40 的记录。

```
const $ = db.command.aggregate
db.collection('price').aggregate()
  .project({
    fullfilled: $.not($.gt(['$min', 40]))
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