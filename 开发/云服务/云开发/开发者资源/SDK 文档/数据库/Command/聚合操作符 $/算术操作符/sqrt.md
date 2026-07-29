# [#](#AggregateCommand-sqrt-value-Expression-Object) <AggregateCommand>.sqrt(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。求平方根。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<number>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.sqrt([<number>])
```

参数可以是任意解析为非负数字的表达式。

## [#](#示例代码) 示例代码

假设直角三角形集合 `triangle` 有如下记录：

```
{ "_id": 1, "x": 2, "y": 3 }
{ "_id": 2, "x": 5, "y": 7 }
{ "_id": 3, "x": 10, "y": 20 }
```

假设 `x` 和 `y` 分别为两直角边，则求斜边长：

```
const $ = db.command.aggregate
db.collection('triangle').aggregate()
  .project({
    len: $.sqrt([$.add([$.pow(['$x', 2]), $.pow(['$y', 2])])]),
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "len": 3.605551275463989 }
{ "_id": 2, "len": 8.602325267042627 }
{ "_id": 3, "len": 22.360679774997898 }
```

Incorrect translation.