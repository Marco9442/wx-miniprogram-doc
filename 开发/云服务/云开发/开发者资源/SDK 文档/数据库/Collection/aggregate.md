# [#](#Collection-aggregate-Aggregate) [Collection](../Collection).aggregate(): [Aggregate](../aggregate/Aggregate)

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

发起[聚合](../../../guide/database/aggregation/aggregation)操作，定义完聚合流水线阶段之后需调用 `end` 方法标志结束定义并实际发起聚合操作

## [#](#返回值) 返回值

### [#](#Aggregate) [Aggregate](../aggregate/Aggregate)

## [#](#示例代码) 示例代码

```
const $ = db.command.aggregate
db.collection('books').aggregate()
  .group({
    // 按 category 字段分组
    _id: '$category',
    // 让输出的每组记录有一个 avgSales 字段，其值是组内所有记录的 sales 字段的平均值
    avgSales: $.avg('$sales')
  })
  .end()
  .then(res => console.log(res))
  .catch(err => console.error(err))
```

小程序端兼容支持 callback 风格

```
const $ = db.command.aggregate
db.collection('books').aggregate()
  .group({
    // 按 category 字段分组
    _id: '$category',
    // 让输出的每组记录有一个 avgSales 字段，其值是组内所有记录的 sales 字段的平均值
    avgSales: $.avg('$sales')
  })
  .end({
    success: function(res) {
      console.log(res)
    },
    fail: function(err) {
      console.error(err)
    }
  })
```

Incorrect translation.