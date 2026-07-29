# [#](#Collection-orderBy-fieldPath-string-string-order-Collection) [Collection](../Collection).orderBy(fieldPath: string, string: order): [Collection](../Collection)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

指定查询排序条件

## [#](#参数) 参数

### [#](#fieldPath-string) fieldPath: string

### [#](#string-order) string: order

## [#](#返回值) 返回值

### [#](#Collection) [Collection](../Collection)

## [#](#说明) 说明

方法接受一个必填字符串参数 fieldName 用于定义需要排序的字段，一个字符串参数 order 定义排序顺序。order 只能取 `asc` 或 `desc`。

如果需要对嵌套字段排序，需要用 "点表示法" 连接嵌套字段，比如 `style.color` 表示字段 `style` 里的嵌套字段 `color`。

同时也支持按多个字段排序，多次调用 `orderBy` 即可，多字段排序时的顺序会按照 `orderBy` 调用顺序先后对多个字段排序

## [#](#示例代码：按一个字段排序) 示例代码：按一个字段排序

按进度排升序取待办事项

```
db.collection('todos').orderBy('progress', 'asc')
  .get()
  .then(console.log)
  .catch(console.error)
```

## [#](#示例代码：按多个字段排序) 示例代码：按多个字段排序

先按 progress 排降序（progress 越大越靠前）、再按 description 排升序（字母序越前越靠前）取待办事项：

```
db.collection('todos')
  .orderBy('progress', 'desc')
  .orderBy('description', 'asc')
  .get()
  .then(console.log)
  .catch(console.error)
```

Incorrect translation.