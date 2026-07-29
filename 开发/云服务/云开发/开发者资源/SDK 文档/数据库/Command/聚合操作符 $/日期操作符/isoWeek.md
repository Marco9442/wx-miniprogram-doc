# [#](#AggregateCommand-isoWeek-value-Expression-string-Object) <AggregateCommand>.isoWeek(value: [Expression](../../aggregate/Expression)<string>): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。返回日期字段对应的 ISO 8601 标准的周数（一年中的第几周），是一个介于 1 到 53 之间的整数。

## [#](#参数) 参数

### [#](#value-Expression-string) value: [Expression](../../aggregate/Expression)<string>

日期字段

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

根据 ISO 8601 标准，周一到周日视为一周，本年度第一个周四所在的那周，视为本年度的第 1 周。

例如：2016 年 1 月 7 日是那年的第一个周四，那么 2016.01.04（周一）到 2016.01.10（周日） 即为第 1 周。同理，2016 年 1 月 1 日的周数为 53。

语法如下：

```
db.command.aggregate.isoWeek(<日期字段>)
```

## [#](#示例代码) 示例代码

假设集合 `dates` 有以下文档：

```
{
    "_id": 1,
    "date": ISODate("2019-05-14T09:38:51.686Z")
}
```

我们使用 `isoWeek()` 对 `date` 字段进行投影，获取对应的 ISO 8601 标准的周数（一年中的第几周）：

```
const $ = db.command.aggregate
db
  .collection('dates')
  .aggregate()
  .project({
    _id: 0,
    isoWeek: $.isoWeek('$date')
  })
  .end()
```

输出如下：

```
{
    "isoWeek": 20
}
```

Incorrect translation.