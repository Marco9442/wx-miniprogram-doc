# [#](#AggregateCommand-log10-value-Expression-number-Object) <AggregateCommand>.log10(value: [Expression](../../aggregate/Expression)<number>): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。计算给定数字在对数底为 10 下的 log 值。

## [#](#参数) 参数

### [#](#value-Expression-number) value: [Expression](../../aggregate/Expression)<number>

number

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.log(<number>)
```

`<number>` 可以是任意解析为非负数字的表达式。

`log10` 等同于 `log` 方法的第二个参数固定为 10。

## [#](#示例代码) 示例代码

## [#](#db-command-aggregate-log10) db.command.aggregate.log10

聚合操作符。计算给定数字在对数底为 10 下的 log 值。

语法如下：

```
db.command.aggregate.log(<number>)
```

`<number>` 可以是任意解析为非负数字的表达式。

`log10` 等同于 `log` 方法的第二个参数固定为 10。

Incorrect translation.