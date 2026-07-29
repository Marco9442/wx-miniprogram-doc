# [#](#AggregateCommand-trunc-value-Expression-number-Object) <AggregateCommand>.trunc(value: [Expression](../../aggregate/Expression)<number>): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。将数字截断为整形。

## [#](#参数) 参数

### [#](#value-Expression-number) value: [Expression](../../aggregate/Expression)<number>

number

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.trunc(<number>)
```

参数可以是任意解析为数字的表达式。

## [#](#示例代码) 示例代码

假设集合 `scores` 有如下记录：

```
{ "_id": 1, "value": 1.21 }
{ "_id": 2, "value": 3.83 }
{ "_id": 3, "value": -4.94 }
```

```
const $ = db.command.aggregate
db.collection('scores').aggregate()
  .project({
    int: $.trunc('$value')
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "value": 1 }
{ "_id": 2, "value": 3 }
{ "_id": 3, "value": -4 }
```

Incorrect translation.