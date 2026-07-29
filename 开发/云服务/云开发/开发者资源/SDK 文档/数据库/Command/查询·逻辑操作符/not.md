# [#](#Command-not-command-Command-Command) [Command](../Command).not(command: [Command](../Command)): [Command](../Command)

> 支持端：[小程序 2.8.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 1.2.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

查询操作符，用于表示逻辑 "非" 的关系，表示需不满足指定的条件。

## [#](#参数) 参数

### [#](#command-Command) command: [Command](../Command)

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例) 示例

如筛选出进度不等于100的 todo：

```
const _ = db.command
db.collection('todo').where({
  progress: _.not(_.eq(100))
})
```

`not` 也可搭配其他逻辑指令使用，包括 `and`, `or`, `nor`, `not`，如 `or`：

```
const _ = db.command
db.collection('todo').where({
  progress: _.not(_.or([_.lt(50), _.eq(100)]))
})
```

Incorrect translation.