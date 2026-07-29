# [#](#Collection-doc-id-string-Document) [Collection](../Collection).doc(id: string): [Document](../Document)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

获取集合中指定记录的引用。方法接受一个 id 参数，指定需引用的记录的 \_id。

## [#](#参数) 参数

### [#](#id-string) id: string

记录 \_id

## [#](#返回值) 返回值

### [#](#Document) [Document](../Document)

## [#](#示例代码) 示例代码

```
const myTodo = db.collection('todos').doc('my-todo-id')
```

Incorrect translation.