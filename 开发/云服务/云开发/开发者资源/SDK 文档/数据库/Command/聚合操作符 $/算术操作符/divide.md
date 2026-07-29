# [#](#AggregateCommand-divide-value-Expression-Object) <AggregateCommand>.divide(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。传入被除数和除数，求商。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<被除数表达式>, <除数表达式>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.divide([<被除数表达式>, <除数表达式>])
```

表达式可以是任意解析为数字的表达式。

## [#](#示例代码) 示例代码

假设集合 `railroads` 有如下记录：

```
{ _id: 1, meters: 5300 }
{ _id: 2, meters: 64000 }
{ _id: 3, meters: 130 }
```

可以用如下方式取各个数字转换为千米之后的值：

```
const $ = db.command.aggregate
db.collection('railroads').aggregate()
  .project({
    km: $.divide(['$meters', 1000])
  })
  .end()
```

返回结果如下：

```
{ _id: 1, km: 5.3 }
{ _id: 2, km: 64 }
{ _id: 3, km: 0.13 }
```

Incorrect translation.