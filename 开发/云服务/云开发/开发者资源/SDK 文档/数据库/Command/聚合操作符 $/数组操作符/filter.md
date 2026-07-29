# [#](#AggregateCommand-filter-value-any-Object) <AggregateCommand>.filter(value: any): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。根据给定条件返回满足条件的数组的子集。

## [#](#参数) 参数

### [#](#value-any) value: any

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.filter({
  input: <array>,
  as: <string>,
  cond: <expression>
})
```

| 字段 | 说明 |
| --- | --- |
| input | 一个可以解析为数组的表达式 |
| as | 可选，用于表示数组各个元素的变量，默认为 this |
| cond | 一个可以解析为布尔值的表达式，用于判断各个元素是否满足条件，各个元素的名字由 `as` 参数决定（参数名需加 `$$` 前缀，如 `$$this`） |

参数可以是任意解析为数组的表达式。

## [#](#示例代码) 示例代码

假设集合 `fruits` 有如下记录：

```
{
  "_id": 1,
  "stock": [
    { "name": "apple", "price": 10 },
    { "name": "orange", "price": 20 }
  ],
}
{
  "_id": 2,
  "stock": [
    { "name": "lemon", "price": 15 },
  ],
}
```

```
const _ = db.command
const $ = db.command.aggregate
db.collection('fruits').aggregate()
  .project({
    stock: $.filter({
      input: '$stock',
      as: 'item',
      cond: $.gte(['$$item.price', 15])
    })
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "stock": [ { "name": "orange", "price": 20} ] }
{ "_id": 2, "stock": [ { "name": "lemon", "price": 15 } ] }
```

Incorrect translation.