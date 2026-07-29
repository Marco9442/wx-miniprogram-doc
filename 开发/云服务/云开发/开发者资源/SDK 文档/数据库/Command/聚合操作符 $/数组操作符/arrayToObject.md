# [#](#AggregateCommand-arrayToObject-value-any-Object) <AggregateCommand>.arrayToObject(value: any): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。将一个数组转换为对象。

## [#](#参数) 参数

### [#](#value-any) value: any

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法可以取两种：

第一种：传入一个二维数组，第二维的数组长度必须为 2，其第一个值为字段名，第二个值为字段值

```
db.command.aggregate.arrayToObject([
  [<key1>, <value1>],
  [<key2>, <value2>],
  ...
])
```

第二种：传入一个对象数组，各个对象必须包含字段 `k` 和 `v`，分别指定字段名和字段值

```
db.command.aggregate.arrayToObject([
  { "k": <key1>, "v": <value1> },
  { "k": <key2>, "v": <value2> },
  ...
])
```

传入 `arrayToObject` 的参数只要可以解析为上述两种表示法之一即可。

## [#](#示例代码) 示例代码

假设集合 `shops` 有如下记录：

```
{ "_id": 1, "sales": [ ["max", 100], ["min", 50] ] }
{ "_id": 2, "sales": [ ["max", 70], ["min", 60] ] }
{ "_id": 3, "sales": [ { "k": "max", "v": 50 }, { "k": "min", "v": 30 } ] }
```

求各个第一次考试的分数和和最后一次的分数：

```
const $ = db.command.aggregate
db.collection('shops').aggregate()
  .project({
    sales: $.arrayToObject('$sales'),
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "sales": { "max": 100, "min": 50 } }
{ "_id": 2, "sales": { "max": 70, "min": 60 } }
{ "_id": 3, "sales": { "max": 50, "min": 30 } }
```

Incorrect translation.