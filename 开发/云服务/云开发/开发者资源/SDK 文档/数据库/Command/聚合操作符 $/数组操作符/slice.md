# [#](#AggregateCommand-slice-value-Expression-Object) <AggregateCommand>.slice(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。类似 JavaScritp 的 `slice` 方法。返回给定数组的指定子集。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<array>, <n>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法有两种：

返回从开头或结尾开始的 `n` 个元素：

```
db.command.aggregate.slice([<array>, <n>])
```

返回从指定位置算作数组开头、再向后或向前的 `n` 个元素：

```
db.command.aggregate.slice([<array>, <position>, <n>])
```

`<array>` 可以是任意解析为数组的表达式。

`<position>` 可以是任意解析为整形的表达式。如果是正数，则将数组的第 `<position>` 个元素作为数组开始；如果 `<position>` 比数组长度更长，`slice` 返回空数组。如果是负数，则将数组倒数第 `<position>` 个元素作为数组开始；如果 `<position>` 的绝对值大于数组长度，则开始位置即为数组开始位置。

`<n>` 可以是任意解析为整形的表达式。如果 `<position>` 有提供，则 `<n>` 必须为正整数。如果是正数，`slice` 返回前 `n` 个元素。如果是负数，`slice` 返回后 `n` 个元素。

## [#](#示例代码) 示例代码

假设集合 `people` 有如下记录：

```
{ "_id": 1, "hobbies": [ "basketball", "football", "tennis", "badminton" ] }
{ "_id": 2, "hobbies": [ "golf", "handball" ] }
{ "_id": 3, "hobbies": [ "table tennis", "swimming", "rowing" ] }
```

统一返回前两个爱好：

```
const $ = db.command.aggregate
db.collection('fruits').aggregate()
  .project({
    hobbies: $.slice(['$hobbies', 2]),
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "hobbies": [ "basketball", "football" ] }
{ "_id": 2, "hobbies": [ "golf", "handball" ] }
{ "_id": 3, "hobbies": [ "table tennis", "swimming" ] }
```

Incorrect translation.