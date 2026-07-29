# [#](#AggregateCommand-log-value-Expression-Object) <AggregateCommand>.log(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。计算给定数字在给定对数底下的 log 值。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<number>, <base>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.log([<number>, <base>])
```

`<number>` 可以是任意解析为非负数字的表达式。`<base>` 可以是任意解析为大于 1 的数字的表达式。

如果任一参数解析为 `null` 或指向任意一个不存在的字段，`log` 返回 `null`。如果任一参数解析为 `NaN`，`log` 返回 `NaN`。

## [#](#示例代码) 示例代码

假设集合 `curve` 有如下记录：

```
{ _id: 1, x: 1 }
{ _id: 2, x: 2 }
{ _id: 3, x: 3 }
```

计算 `log2(x)` 的值：

```
const $ = db.command.aggregate
db.collection('staff').aggregate()
  .project({
    log: $.log(['$x', 2])
  })
  .end()
```

返回结果如下：

```
{ _id: 1, log: 0 }
{ _id: 2, log: 1 }
{ _id: 3, log: 1.58496250072 }
```

Incorrect translation.