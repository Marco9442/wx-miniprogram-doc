# [#](#Command-pullAll-value-any-Command) [Command](../Command).pullAll(value: any): [Command](../Command)

> 支持端：[小程序 2.8.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 1.2.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

数组更新操作符。给定一个值或一个查询条件，将数组中所有匹配给定值的元素都移除掉。跟 `pull` 的差别在于只能指定常量值、传入的是数组。

## [#](#参数) 参数

### [#](#value-any) value: any

值或查询条件

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例代码：根据常量匹配移除) 示例代码：根据常量匹配移除

从 tags 中移除所有 database 和 cloud 字符串

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    tags: _.pullAll(['database', 'cloud'])
  }
})
```

Incorrect translation.