# [#](#AggregateCommand-floor-value-Expression-number-Object) <AggregateCommand>.floor(value: [Expression](../../aggregate/Expression)<number>): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。向下取整，返回大于或等于给定数字的最小整数。

## [#](#参数) 参数

### [#](#value-Expression-number) value: [Expression](../../aggregate/Expression)<number>

number

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.floor(<number>)
```

`<number>` 可以是任意解析为数字的表达式。如果表达式解析为 `null` 或指向一个不存在的字段，则返回 `null`，如果解析为 `NaN`，则返回 `NaN`。

## [#](#示例代码) 示例代码

假设集合 `sales` 有如下记录：

```
{ _id: 1, sales: 5.2 }
{ _id: 2, sales: 1.32 }
{ _id: 3, sales: -3.2 }
```

可以用如下方式取各个数字的向下取整值：

```
const $ = db.command.aggregate
db.collection('sales').aggregate()
  .project({
    sales: $.floor('$sales')
  })
  .end()
```

返回结果如下：

```
{ _id: 1, sales: 5 }
{ _id: 2, sales: 1 }
{ _id: 3, sales: -4 }
```

Incorrect translation.