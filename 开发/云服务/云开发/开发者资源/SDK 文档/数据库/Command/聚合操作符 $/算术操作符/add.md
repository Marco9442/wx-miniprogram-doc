# [#](#AggregateCommand-add-value-Expression-Object) <AggregateCommand>.add(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。将数字相加或将数字加在日期上。如果数组中的其中一个值是日期，那么其他值将被视为毫秒数加在该日期上。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<表达式1>, <表达式2>, ...]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.add([<表达式1>, <表达式2>, ...])
```

表达式可以是形如 `$ + 指定字段`，也可以是普通字符串。只要能够被解析成字符串即可。

## [#](#示例代码) 示例代码

假设集合 `staff` 有如下记录：

```
{ _id: 1, department: "x", sales: 5, engineer: 10, lastUpdate: ISODate("2019-05-01T00:00:00Z") }
{ _id: 2, department: "y", sales: 10, engineer: 20, lastUpdate: ISODate("2019-05-01T02:00:00Z") }
{ _id: 3, department: "z", sales: 20, engineer: 5, lastUpdate: ISODate("2019-05-02T03:00:00Z") }
```

#### [#](#数字求和) 数字求和

可以用如下方式求得各个记录人数总数：

```
const $ = db.command.aggregate
db.collection('staff').aggregate()
  .project({
    department: 1,
    total: $.add(['$sales', '$engineer'])
  })
  .end()
```

返回结果如下：

```
{ _id: 1, department: "x", total: 15 }
{ _id: 2, department: "y", total: 30 }
{ _id: 3, department: "z", total: 25 }
```

#### [#](#增加日期值) 增加日期值

如下操作可以获取各个记录的 `lastUpdate` 加一个小时之后的值：

```
const $ = db.command.aggregate
db.collection('staff').aggregate()
  .project({
    department: 1,
    lastUpdate: $.add(['$lastUpdate', 60*60*1000])
  })
  .end()
```

返回结果如下：

```
{ _id: 1, department: "x", lastUpdate: ISODate("2019-05-01T01:00:00Z") }
{ _id: 2, department: "y", lastUpdate: ISODate("2019-05-01T03:00:00Z") }
{ _id: 3, department: "z", lastUpdate: ISODate("2019-05-02T04:00:00Z") }
```

Incorrect translation.