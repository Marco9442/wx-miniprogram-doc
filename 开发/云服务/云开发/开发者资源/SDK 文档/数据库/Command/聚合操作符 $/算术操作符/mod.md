# [#](#AggregateCommand-mod-value-Expression-Object) <AggregateCommand>.mod(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。取模运算，取数字取模后的值。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<dividend>, <divisor>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.mod([<dividend>, <divisor>])
```

第一个数字是被除数，第二个数字是除数。参数可以是任意解析为数字的表达式。

## [#](#示例代码) 示例代码

假设集合 `shopping` 有如下记录：

```
{ _id: 1, bags: 3, items: 5 }
{ _id: 2, bags: 2, items: 8 }
{ _id: 3, bags: 5, items: 16 }
```

各记录取 `items` 除以 `bags` 的余数（`items % bags`）：

```
const $ = db.command.aggregate
db.collection('shopping').aggregate()
  .project({
    overflow: $.mod(['$items', '$bags'])
  })
  .end()
```

返回结果如下：

```
{ _id: 1, log: 2 }
{ _id: 2, log: 0 }
{ _id: 3, log: 1 }
```

Incorrect translation.