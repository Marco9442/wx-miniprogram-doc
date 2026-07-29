# [#](#AggregateCommand-ifNull-value-Expression-Object) <AggregateCommand>.ifNull(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。计算给定的表达式，如果表达式结果为 null、undefined 或者不存在，那么返回一个替代值；否则返回原值。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[ <表达式>, <替代值> ]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`ifNull` 的使用形式如下：

```
ifNull([ <表达式>, <替代值> ])
```

## [#](#示例代码) 示例代码

假设集合 `items` 的记录如下：

```
{ "_id": "0", "name": "A", "description": "这是商品A" }
{ "_id": "1", "name": "B", "description": null }
{ "_id": "2", "name": "C" }
```

我们可以使用 `ifNull`，对不存在 `desc` 字段的文档，或者 `desc` 字段为 `null` 的文档，补充一个替代值。

```
const $ = db.command.aggregate
db.collection('items').aggregate()
  .project({
    _id: 0,
    name: 1,
    description: $.ifNull(['$description', '商品描述空缺'])
  })
  .end()
```

输出如下：

```
{ "name": "A", "description": "这是商品A" }
{ "name": "B", "description": "商品描述空缺" }
{ "name": "C", "description": "商品描述空缺" }
```

Incorrect translation.