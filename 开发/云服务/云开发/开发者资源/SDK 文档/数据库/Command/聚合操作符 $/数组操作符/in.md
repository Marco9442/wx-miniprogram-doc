# [#](#AggregateCommand-in-value-Expression-Object) <AggregateCommand>.in(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。给定一个值和一个数组，如果值在数组中则返回 `true`，否则返回 `false`。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<value>, <array>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.in([<value>, <array>])
```

`<value>` 可以是任意表达式。

`<array>` 可以是任意解析为数组的表达式。

## [#](#示例代码) 示例代码

假设集合 `shops` 有如下记录：

```
{ "_id": 1, "topsellers": ["bread", "ice cream", "butter"] }
{ "_id": 2, "topsellers": ["ice cream", "cheese", "yagurt"] }
{ "_id": 3, "topsellers": ["croissant", "cucumber", "coconut"] }
```

标记销量最高的商品包含 `ice cream` 的记录。

```
const $ = db.command.aggregate
db.collection('price').aggregate()
  .project({
    included: $.in(['ice cream', '$topsellers'])
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "included": true }
{ "_id": 2, "included": true }
{ "_id": 3, "included": false }
```

Incorrect translation.