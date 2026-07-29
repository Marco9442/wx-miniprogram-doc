# [#](#Collection-field-projection-Object-Collection) [Collection](../Collection).field(projection: Object): [Collection](../Collection)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

指定返回结果中记录需返回的字段

## [#](#参数) 参数

### [#](#projection-Object) projection: Object

## [#](#返回值) 返回值

### [#](#Collection) [Collection](../Collection)

## [#](#说明) 说明

方法接受一个必填对象用于指定需返回的字段，对象的各个 key 表示要返回或不要返回的字段，value 传入 true|false（或 1|-1）表示要返回还是不要返回。

## [#](#示例代码) 示例代码

只返回 description, done 和 progress 三个字段：

```
db.collection('todos').field({
  description: true,
  done: true,
  progress: true,
})
  .get()
  .then(console.log)
  .catch(console.error)
```

Incorrect translation.