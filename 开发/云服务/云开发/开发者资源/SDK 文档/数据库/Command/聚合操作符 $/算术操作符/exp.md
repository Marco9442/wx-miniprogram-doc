# [#](#AggregateCommand-exp-value-Expression-number-Object) <AggregateCommand>.exp(value: [Expression](../../aggregate/Expression)<number>): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。取 e（自然对数的底数，欧拉数） 的 n 次方。

## [#](#参数) 参数

### [#](#value-Expression-number) value: [Expression](../../aggregate/Expression)<number>

exponent

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.exp(<exponent>)
```

`<exponent>` 可以是任意解析为数字的表达式。如果表达式解析为 `null` 或指向一个不存在的字段，则返回 `null`，如果解析为 `NaN`，则返回 `NaN`。

## [#](#示例代码) 示例代码

假设集合 `math` 有如下记录：

```
{ _id: 1, exp: 0 }
{ _id: 2, exp: 1 }
{ _id: 3, exp: 2 }
```

```
const $ = db.command.aggregate
db.collection('math').aggregate()
  .project({
    result: $.exp('$exp')
  })
  .end()
```

返回结果如下：

```
{ _id: 1, result: 1 }
{ _id: 2, result: 2.71828182845905 }
{ _id: 3, result: 7.38905609893065 }
```

Incorrect translation.