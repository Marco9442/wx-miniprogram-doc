# [#](#Collection-skip-offset-number-Collection) [Collection](../Collection).skip(offset: number): [Collection](../Collection)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

指定查询返回结果时从指定序列后的结果开始返回，常用于分页

## [#](#参数) 参数

### [#](#offset-number) offset: number

## [#](#返回值) 返回值

### [#](#Collection) [Collection](../Collection)

## [#](#示例代码) 示例代码

```
db.collection('todos').skip(10)
  .get()
  .then(console.log)
  .catch(console.error)
```

Incorrect translation.