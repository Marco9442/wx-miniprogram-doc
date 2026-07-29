# [#](#AggregateCommand-dateFromString-value-any-Object) <AggregateCommand>.dateFromString(value: any): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。将一个日期/时间字符串转换为日期对象

## [#](#参数) 参数

### [#](#value-any) value: any

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.dateFromString({
    dateString: <dateStringExpression>,
    timezone: <tzExpression>
})
```

## [#](#示例代码) 示例代码

```
const $ = db.command.aggregate
db
  .collection('dates')
  .aggregate()
  .project({
    _id: 0,
    date: $.dateFromString({
        dateString: "2019-05-14T09:38:51.686Z"
    })
  })
  .end()
```

输出如下：

```
{
    "date": ISODate("2019-05-14T09:38:51.686Z")
}
```

Incorrect translation.