# [#](#AggregateCommand-indexOfArray-value-Expression-Object) <AggregateCommand>.indexOfArray(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。在数组中找出等于给定值的第一个元素的下标，如果找不到则返回 -1。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[ <array expression>, <search expression>, <start>, <end> ]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.indexOfArray([ <array expression>, <search expression>, <start>, <end> ])
```

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| `<array>` | string | 一个可以解析为数组的表达式，如果解析为 null，则 `indexOfArray` 返回 null |
| `<search>` | string | 对数据各个元素应用的条件匹配表达式 |
| `<start>` | integer | 可选，用于指定搜索的开始下标，必须是非负整数 |
| `<end>` | integer | 可选，用于指定搜索的结束下标，必须是非负整数，指定了 `<end>` 时也应指定 `<start>`，否则 `<end>` 默认当做 `<start>` |

参数可以是任意解析为数组的表达式。

## [#](#示例代码) 示例代码

假设集合 `stats` 有如下记录：

```
{
  "_id": 1,
  "sales": [ 1, 6, 2, 2, 5 ]
}
{
  "_id": 2,
  "sales": [ 4, 2, 1, 5, 2 ]
}
{
  "_id": 3,
  "sales": [ 2, 5, 3, 3, 1 ]
}
```

```
const $ = db.command.aggregate
db.collection('stats').aggregate()
  .project({
    index: $.indexOfArray(['$sales', 2, 2])
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "index": 2 }
{ "_id": 2, "index": 4 }
{ "_id": 3, "index": -1 }
```

Incorrect translation.