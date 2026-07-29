# [#](#AggregateCommand-size-value-Expression-any-Object) <AggregateCommand>.size(value: [Expression](../../aggregate/Expression)<any[]>): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。返回数组长度。

## [#](#参数) 参数

### [#](#value-Expression-any) value: [Expression](../../aggregate/Expression)<any[]>

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.size(<array>)
```

`<array>` 可以是任意解析为数组的表达式。

## [#](#示例代码) 示例代码

假设集合 `shops` 有如下记录：

```
{ "_id": 1, "staff": [ "John", "Middleton", "George" ] }
{ "_id": 2, "staff": [ "Steph", "Jack" ] }
```

计算各个商店的雇员数量：

```
const $ = db.command.aggregate
db.collection('staff').aggregate()
  .project({
    totalStaff: $.size('$staff')
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "totalStaff": 3 }
{ "_id": 2, "totalStaff": 2 }
```

Incorrect translation.