# [#](#Collection-limit-value-number-Collection) [Collection](../Collection).limit(value: number): [Collection](../Collection)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

指定查询结果集数量上限

## [#](#参数) 参数

### [#](#value-number) value: number

## [#](#返回值) 返回值

### [#](#Collection) [Collection](../Collection)

## [#](#说明) 说明

`limit` 在小程序端默认及最大上限为 20，在云函数端默认及最大上限为 1000

## [#](#示例代码) 示例代码

```
db.collection('todos').limit(10)
  .get()
  .then(console.log)
  .catch(console.error)
```

Incorrect translation.