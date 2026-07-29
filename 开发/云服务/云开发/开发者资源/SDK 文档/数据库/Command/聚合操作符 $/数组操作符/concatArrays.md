# [#](#AggregateCommand-concatArrays-value-Expression-Object) <AggregateCommand>.concatArrays(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。将多个数组拼接成一个数组。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[ <array1>, <array2>, ... ]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.arrayToObject([ <array1>, <array2>, ... ])
```

参数可以是任意解析为数组的表达式。

## [#](#示例代码) 示例代码

假设集合 `items` 有如下记录：

```
{ "_id": 1, "fruits": [ "apple" ], "vegetables": [ "carrot" ] }
{ "_id": 2, "fruits": [ "orange", "lemon" ], "vegetables": [ "cabbage" ] }
{ "_id": 3, "fruits": [ "strawberry" ], "vegetables": [ "spinach" ] }
```

```
const $ = db.command.aggregate
db.collection('items').aggregate()
  .project({
    list: $.concatArrays(['$fruits', '$vegetables']),
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "list": [ "apple", "carrot" ] }
{ "_id": 2, "list": [ "orange", "lemon", "cabbage" ] }
{ "_id": 3, "list": [ "strawberry", "spinach" ] }
```

Incorrect translation.