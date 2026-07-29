# [#](#AggregateCommand-sum-value-Expression-Object) <AggregateCommand>.sum(value: [Expression](../../aggregate/Expression)): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。计算并且返回一组字段所有数值的总和。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)

表达式

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`sum` 的使用形式如下：

```
db.command.aggregate.sum(<表达式>)
```

表达式可以传入指定字段，也可以传入指定字段组成的列表。`sum` 会自动忽略非数字值。如果字段下的所有值均是非数字，那么结果返回 0。若传入数字常量，则当做所有记录该字段的值都给给定常量，在聚合时相加，最终值为输入记录数乘以常量。

## [#](#示例代码) 示例代码

假设代表商品的集合 `goods` 的记录如下：`price` 代表商品销售额，`cost` 代表商品成本

```
{ "cost": -10, "price": 100 }
{ "cost": -15, "price": 1 }
{ "cost": -10, "price": 10 }
```

#### [#](#单独字段) 单独字段

借助 `sum` 可以计算所有商品的销售总和，代码如下：

```
const $ = db.command.aggregate
db
  .collection('goods')
  .aggregate()
  .group({
    _id: null,
    totalPrice: $.sum('$price')
  })
  .end()
```

返回的数据结果如下：销售额是 111

```
{ "_id": null, "totalPrice": 111 }
```

#### [#](#字段列表) 字段列表

如果需要计算所有商品的利润总额，那么需要将每条记录的 `cost` 和 `price` 相加得到此记录对应商品的利润。最后再计算所有商品的利润总额。

借助 `sum`，代码如下：

```
const $ = db.command.aggregate
db
  .collection('goods')
  .aggregate()
  .group({
    _id: null,
    totalProfit: $.sum(
      $.sum(['$price', '$cost'])
    )
  })
  .end()
```

返回的数据结果如下：利润总额为 76

```
{ "_id": null, "totalProfit": 76 }
```

Incorrect translation.