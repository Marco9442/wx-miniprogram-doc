# [#](#AggregateCommand-reverseArray-value-Expression-any-Object) <AggregateCommand>.reverseArray(value: [Expression](../../aggregate/Expression)<any[]>): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。返回给定数组的倒序形式。

## [#](#参数) 参数

### [#](#value-Expression-any) value: [Expression](../../aggregate/Expression)<any[]>

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.reverseArray(<array>)
```

参数可以是任意解析为数组表达式。

## [#](#示例代码) 示例代码

假设集合 `stats` 有如下记录：

```
{
  "_id": 1,
  "sales": [ 1, 2, 3, 4, 5 ]
}
```

取 `sales` 倒序：

```
const $ = db.command.aggregate
db.collection('stats').aggregate()
  .project({
    reversed: $.reverseArray('$sales'),
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "reversed": [5, 4, 3, 2, 1] }
```

Incorrect translation.