# [#](#AggregateCommand-ln-value-Expression-number-Object) <AggregateCommand>.ln(value: [Expression](../../aggregate/Expression)<number>): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。计算给定数字在自然对数值。

## [#](#参数) 参数

### [#](#value-Expression-number) value: [Expression](../../aggregate/Expression)<number>

number

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.ln(<number>)
```

`<number>` 可以是任意解析为非负数字的表达式。

`ln` 等价于 `log([<number>, Math.E])`，其中 `Math.E` 是 `JavaScript` 获取 `e` 的值的方法。

## [#](#示例代码) 示例代码

## [#](#db-command-aggregate-ln) db.command.aggregate.ln

聚合操作符。计算给定数字在自然对数值。

语法如下：

```
db.command.aggregate.ln(<number>)
```

`<number>` 可以是任意解析为非负数字的表达式。

`ln` 等价于 `log([<number>, Math.E])`，其中 `Math.E` 是 `JavaScript` 获取 `e` 的值的方法。

Incorrect translation.