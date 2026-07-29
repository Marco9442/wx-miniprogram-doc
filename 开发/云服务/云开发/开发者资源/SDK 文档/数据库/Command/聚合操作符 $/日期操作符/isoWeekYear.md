# [#](#AggregateCommand-isoWeekYear-value-Expression-string-Object) <AggregateCommand>.isoWeekYear(value: [Expression](../../aggregate/Expression)<string>): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。返回日期字段对应的 ISO 8601 标准的天数（一年中的第几天）。

## [#](#参数) 参数

### [#](#value-Expression-string) value: [Expression](../../aggregate/Expression)<string>

日期字段

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

此处的“年”以第一周的周一为开始，以最后一周的周日为结束。

语法如下：

```
db.command.aggregate.isoWeekYear(<日期字段>)
```

## [#](#示例代码) 示例代码

假设集合 `dates` 有以下文档：

```
{
    "_id": 1,
    "date": ISODate("2019-05-14T09:38:51.686Z")
}
```

我们使用 `isoWeekYear()` 对 `date` 字段进行投影，获取对应的 ISO 8601 标准的天数（一年中的第几天）：

```
const $ = db.command.aggregate
db
  .collection('dates')
  .aggregate()
  .project({
    _id: 0,
    isoWeekYear: $.isoWeekYear('$date')
  })
  .end()
```

输出如下：

```
{
    "isoWeekYear": 2019
}
```

Incorrect translation.