# [#](#AggregateCommand-lte-value-Expression-Object) <AggregateCommand>.lte(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。匹配两个值，如果前者小于或等于后者则返回 `true`，否则返回 `false`。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<value1>, <value2>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.lte([<value1>, <value2>])
```

## [#](#示例代码) 示例代码

假设集合 `price` 有如下记录：

```
{ "_id": 1, "value": 10 }
{ "_id": 2, "value": 80 }
{ "_id": 3, "value": 50 }
```

判断 `value` 是否小于 50。

```
const $ = db.command.aggregate
db.collection('price').aggregate()
  .project({
    matched: $.lte(['$value', 50])
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "matched": true }
{ "_id": 2, "matched": false }
{ "_id": 3, "matched": true }
```

Incorrect translation.