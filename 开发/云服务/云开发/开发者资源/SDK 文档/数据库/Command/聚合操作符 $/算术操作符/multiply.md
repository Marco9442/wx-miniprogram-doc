# [#](#AggregateCommand-multiply-value-Expression-Object) <AggregateCommand>.multiply(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。取传入的数字参数相乘的结果。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<expression1>, <expression2>, ...]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.multiply([<expression1>, <expression2>, ...])
```

参数可以是任意解析为数字的表达式。

## [#](#示例代码) 示例代码

假设集合 `fruits` 有如下记录：

```
{ "_id": 1, "name": "apple", "price": 10, "quantity": 100 }
{ "_id": 2, "name": "orange", "price": 15, "quantity": 50 }
{ "_id": 3, "name": "lemon", "price": 5, "quantity": 20 }
```

求各个水果的的总价值：

```
const $ = db.command.aggregate
db.collection('fruits').aggregate()
  .project({
    name: 1,
    total: $.multiply(['$price', '$quantity']),
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "name": "apple", "total": 1000 }
{ "_id": 2, "name": "orange", "total": 750 }
{ "_id": 3, "name": "lemo", "total": 100 }
```

Incorrect translation.