# [#](#AggregateCommand-setEquals-value-Expression-Object) <AggregateCommand>.setEquals(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符，输入两个集合，判断两个集合中包含的元素是否相同（不考虑顺序、去重）。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<expression1>, <expression2>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

使用形式如下：

```
setEquals([<expression1>, <expression2>])
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

下面的代码使用 `setEquals`，判断两个集合中包含的元素是否相同：

```
db.collection('test')
  .aggregate()
  .project({
    sameElements: $.setEquals(['$A', '$B'])
  })
  .end()
```

```
{ "_id": 1, "sameElements": true }
{ "_id": 2, "sameElements": true }
{ "_id": 3, "sameElements": false }
{ "_id": 4, "sameElements": false }
{ "_id": 5, "sameElements": false }
{ "_id": 6, "sameElements": false }
{ "_id": 7, "sameElements": true }
{ "_id": 8, "sameElements": false }
```

Incorrect translation.