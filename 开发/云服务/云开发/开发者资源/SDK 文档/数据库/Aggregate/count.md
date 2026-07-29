# [#](#Aggregate-count-fieldName-string-Aggregate) <Aggregate>.count(fieldName: string): <Aggregate>

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

聚合阶段。计算上一聚合阶段输入到本阶段的记录数，输出一个记录，其中指定字段的值为记录数。

## [#](#参数) 参数

### [#](#fieldName-string) fieldName: string

## [#](#返回值) 返回值

### [#](#Aggregate) <Aggregate>

## [#](#API-说明) API 说明

`count` 的形式如下：

```
count(<string>)
```

`<string>` 是输出记录数的字段的名字，不能是空字符串，不能以 `$` 开头，不能包含 `.` 字符。

`count` 阶段等同于 `group` + `project` 的操作：

```
const $ = db.command.aggregate
db.collection('items').aggregate()
  .group({
    _id: null,
    count: $.sum(1),
  })
  .project({
    _id: 0,
  })
  .end()
```

上述操作会输出一个包含 `count` 字段的记录。

## [#](#示例) 示例

假设集合 `items` 有如下记录：

```
{
  _id: "1",
  price: 10.5
}
{
  _id: "2",
  price: 50.3
}
{
  _id: "3",
  price: 20.8
}
{
  _id: "4",
  price: 80.2
}
{
  _id: "5",
  price: 200.3
}
```

找出价格大于 50 的记录数：

```
const _ = db.command
db.collection('items').aggregate()
  .match({
    price: _.gt(50)
  })
  .count('expensiveCount')
  .end()
```

返回结果如下：

```
{
  "expensiveCount": 3
}
```

Incorrect translation.