# [#](#AggregateCommand-pow-value-Expression-Object) <AggregateCommand>.pow(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。求给定基数的指数次幂。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<base>, <exponent>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.pow([<base>, <exponent>])
```

参数可以是任意解析为数字的表达式。

## [#](#示例代码) 示例代码

假设集合 `stats` 有如下记录：

```
{ "_id": 1, "x": 2, "y": 3 }
{ "_id": 2, "x": 5, "y": 7 }
{ "_id": 3, "x": 10, "y": 20 }
```

求 `x` 和 `y` 的平方和：

```
const $ = db.command.aggregate
db.collection('stats').aggregate()
  .project({
    sumOfSquares: $.add([$.pow(['$x', 2]), $.pow(['$y', 2])]),
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "sumOfSquares": 13 }
{ "_id": 2, "sumOfSquares": 74 }
{ "_id": 3, "sumOfSquares": 500 }
```

Incorrect translation.