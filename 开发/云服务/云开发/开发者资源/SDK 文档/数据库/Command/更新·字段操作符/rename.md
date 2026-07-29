# [#](#Command-rename-value-string-Command) [Command](../Command).rename(value: string): [Command](../Command)

> 支持端：[小程序 2.8.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 1.2.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

更新操作符，字段重命名。如果需要对嵌套深层的字段做重命名，需要用点路径表示法。不能对嵌套在数组里的对象的字段进行重命名。

## [#](#参数) 参数

### [#](#value-string) value: string

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例-1：重命名顶层字段) 示例 1：重命名顶层字段

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    progress: _.rename('totalProgress')
  }
})
```

## [#](#示例-2：重命名嵌套字段) 示例 2：重命名嵌套字段

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    someObject: {
      someField: _.rename('someObject.renamedField')
    }
  }
})
```

或：

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    'someObject.someField': _.rename('someObject.renamedField')
  }
})
```

Incorrect translation.