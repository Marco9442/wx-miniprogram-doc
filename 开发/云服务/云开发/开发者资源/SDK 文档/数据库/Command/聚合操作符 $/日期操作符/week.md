# [#](#AggregateCommand-week-value-Expression-string-Object) <AggregateCommand>.week(value: [Expression](../../aggregate/Expression)<string>): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。返回日期字段对应的周数（一年中的第几周），是一个介于 0 到 53 之间的整数。

## [#](#参数) 参数

### [#](#value-Expression-string) value: [Expression](../../aggregate/Expression)<string>

日期字段

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

每周以周日为开头，**每年的第一个周日**即为 `week 1` 的开始，这天之前是 `week 0`。

语法如下：

```
db.command.aggregate.week(<日期字段>)
```

## [#](#示例代码) 示例代码

假设集合 `dates` 有以下文档：

```
{
    "_id": 1,
    "date": ISODate("2019-05-14T09:38:51.686Z")
}
```

我们使用 `week()` 对 `date` 字段进行投影，获取对应的周数（一年中的第几周）：

```
const $ = db.command.aggregate
db
  .collection('dates')
  .aggregate()
  .project({
    _id: 0,
    week: $.week('$date')
  })
  .end()
```

输出如下：

```
{
    "week": 19
}
```

Incorrect translation.