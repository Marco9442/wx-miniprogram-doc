# [#](#AggregateCommand-setUnion-value-Expression-Object) <AggregateCommand>.setUnion(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符，输入两个集合，输出两个集合的并集。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<expression1>, <expression2>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

使用形式如下：

```
setUnion([<expression1>, <expression2>])
```

## [#](#示例代码) 示例代码

假设集合 `test` 存在以下数据：

```
{ "_id": 1, "A": [ 1, 2 ], "B": [ 1, 2 ] }
{ "_id": 2, "A": [ 1, 2 ], "B": [ 2, 1, 2 ] }
{ "_id": 3, "A": [ 1, 2 ], "B": [ 1, 2, 3 ] }
{ "_id": 4, "A": [ 1, 2 ], "B": [ 3, 1 ] }
{ "_id": 5, "A": [ 1, 2 ], "B": [ ] }
{ "_id": 6, "A": [ 1, 2 ], "B": [ {}, [] ] }
{ "_id": 7, "A": [ ], "B": [ ] }
{ "_id": 8, "A": [ ], "B": [ 1 ] }
```

下面的代码使用 `setUnion`，输出两个集合的并集：

```
db.collection('test')
  .aggregate()
  .project({
    AB: $.setUnion(['$A', '$B'])
  })
  .end()
```

输出如下：

```
{ "_id": 1, "AB": [ 1, 2 ] }
{ "_id": 2, "AB": [ 1, 2 ] }
{ "_id": 3, "AB": [ 1, 2, 3 ] }
{ "_id": 4, "AB": [ 1, 2, 3 ] }
{ "_id": 5, "AB": [ 1, 2 ] }
{ "_id": 6, "AB": [ 1, 2, {}, [] ] }
{ "_id": 7, "AB": [ ] }
{ "_id": 8, "AB": [ 1 ] }
```

Incorrect translation.