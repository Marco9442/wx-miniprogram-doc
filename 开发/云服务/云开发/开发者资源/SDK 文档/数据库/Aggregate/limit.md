# [#](#Aggregate-limit-value-number-Aggregate) <Aggregate>.limit(value: number): <Aggregate>

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

聚合阶段。限制输出到下一阶段的记录数。

## [#](#参数) 参数

### [#](#value-number) value: number

正整数

## [#](#返回值) 返回值

### [#](#Aggregate) <Aggregate>

## [#](#示例) 示例

假设集合 `items` 有如下记录：

```
{
  _id: "1",
  price: 10
}
{
  _id: "2",
  price: 50
}
{
  _id: "3",
  price: 20
}
{
  _id: "4",
  price: 80
}
{
  _id: "5",
  price: 200
}
```

返回价格大于 20 的记录的最小的两个记录：

```
const $ = db.command.aggregate
db.collection('items').aggregate()
  .match({
    price: $.gt(20)
  })
  .sort({
    price: 1,
  })
  .limit(2)
  .end()
```

返回结果如下：

```
{
  "_id": "3",
  "price": 50
}
{
  "_id": "4",
  "price": 80
}
```

Incorrect translation.