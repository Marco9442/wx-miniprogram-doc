# [#](#Command-remove-Command) [Command](../Command).remove(): [Command](../Command)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

更新操作符，用于表示删除某个字段。

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例代码) 示例代码

删除 style 字段：

```
const _ = db.command
db.collection('todos').doc('todo-id').update({
  data: {
    style: _.remove()
  }
})
```

Incorrect translation.