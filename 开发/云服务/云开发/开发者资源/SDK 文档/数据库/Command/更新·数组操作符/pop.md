# [#](#Command-pop-Command) [Command](../Command).pop(): [Command](../Command)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

数组更新操作符，对一个值为数组的字段，将数组尾部元素删除

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例代码) 示例代码

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    tags: _.pop()
  }
})
```

Incorrect translation.