# [#](#AggregateCommand-isArray-value-Expression-Object) <AggregateCommand>.isArray(value: [Expression](../../aggregate/Expression)): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。判断给定表达式是否是数组，返回布尔值。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)

表达式

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.isArray(<expression>)
```

参数可以是任意表达式。

## [#](#示例代码) 示例代码

假设集合 `stats` 有如下记录：

```
{
  "_id": 1,
  "base": 10,
  "sales": [ 1, 6, 2, 2, 5 ]
}
{
  "_id": 2,
  "base": 1,
  "sales": 100
}
```

计算总销量，如果 `sales` 是数字，则求 `sales * base`，如果 `sales` 是数组，则求数组元素之和与 `base` 的乘积。

```
const $ = db.command.aggregate
db.collection('stats').aggregate()
  .project({
    sum: $.cond({
      if: $.isArray('$sales'),
      then: $.multiply([$.sum(['$sales']), '$base']),
      else: $.multiply(['$sales', '$base']),
    })
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "index": 160 }
{ "_id": 2, "index": 100 }
```

Incorrect translation.