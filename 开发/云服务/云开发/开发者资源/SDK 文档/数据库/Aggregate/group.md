# [#](#Aggregate-group-object-Object-Aggregate) <Aggregate>.group(object: Object): <Aggregate>

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

聚合阶段。将输入记录按给定表达式分组，输出时每个记录代表一个分组，每个记录的 `_id` 是区分不同组的 key。输出记录中也可以包括累计值，将输出字段设为累计值即会从该分组中计算累计值。

## [#](#参数) 参数

### [#](#object-Object) object: Object

## [#](#返回值) 返回值

### [#](#Aggregate) <Aggregate>

## [#](#API-说明) API 说明

`group` 的形式如下：

```
group({
  _id: <expression>,
  <field1>: <accumulator1>,
  ...
  <fieldN>: <accumulatorN>
})
```

`_id` 参数是必填的，如果填常量则只有一组。其他字段是可选的，都是累计值，用 `$.sum` 等累计器，但也可以使用其他表达式。

累计器必须是以下操作符之一：

- addToSet
- avg
- first
- last
- max
- min
- push
- stdDevPop
- stdDevSamp
- sum

#### [#](#内存限制) 内存限制

该阶段有 100M 内存使用限制。

## [#](#示例-1：按字段值分组) 示例 1：按字段值分组

假设集合 `avatar` 有如下记录：

```
{
  _id: "1",
  alias: "john",
  region: "asia",
  scores: [40, 20, 80],
  coins: 100
}
{
  _id: "2",
  alias: "arthur",
  region: "europe",
  scores: [60, 90],
  coins: 20
}
{
  _id: "3",
  alias: "george",
  region: "europe",
  scores: [50, 70, 90],
  coins: 50
}
{
  _id: "4",
  alias: "john",
  region: "asia",
  scores: [30, 60, 100, 90],
  coins: 40
}
{
  _id: "5",
  alias: "george",
  region: "europe",
  scores: [20],
  coins: 60
}
{
  _id: "6",
  alias: "john",
  region: "asia",
  scores: [40, 80, 70],
  coins: 120
}
```

```
const $ = db.command.aggregate
db.collection('avatar').aggregate()
  .group({
    _id: '$alias',
    num: $.sum(1)
  })
  .end()
```

返回结果如下：

```
{
  "_id": "john",
  "num": 3
}
{
  "_id": "authur",
  "num": 1
}
{
  "_id": "george",
  "num": 2
}
```

## [#](#示例-2：按多个值分组) 示例 2：按多个值分组

可以给 `_id` 传入记录的方式按多个值分组。还是沿用上面的示例数据，按各个区域（region）获得相同最高分（score）的来分组，并求出各组虚拟币（coins）的总量：

```
const $ = db.command.aggregate
db.collection('avatar').aggregate()
  .group({
    _id: {
      region: '$region',
      maxScore: $.max('$scores')
    },
    totalCoins: $.sum('$coins')
  })
  .end()
```

返回结果如下：

```
{
  "_id": {
    "region": "asia",
    "maxScore": 80
  },
  "totalCoins": 220
}
{
  "_id": {
    "region": "asia",
    "maxScore": 100
  },
  "totalCoins": 100
}
{
  "_id": {
    "region": "europe",
    "maxScore": 90
  },
  "totalCoins": 70
}
{
  "_id": {
    "region": "europe",
    "maxScore": 20
  },
  "totalCoins": 60
}
```

Incorrect translation.