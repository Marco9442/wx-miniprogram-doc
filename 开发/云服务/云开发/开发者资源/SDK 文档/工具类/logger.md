# [#](#Cloud-logger-Object) [Cloud](../Cloud).logger(): Object

> 支持端：[云函数 1.5.0](../../reference/changelog-server-sdk)

云函数中使用[高级日志](../../guide/functions/logservice)能力

## [#](#返回值) 返回值

### [#](#Object) Object

logger

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| log | function | 默认等级的日志 |
| info | function | 普通等级的日志 |
| warn | function | 警告等级的日志 |
| error | function | 错误等级的日志 |

## [#](#使用说明) 使用说明

用于使用[高级日志](../../guide/functions/logservice)能力。

`logger` 方法返回一个 `log` 对象，`log` 对象包含以下方法，每调用一次产生一条日志记录：
`log`：默认等级的日志
`info`：普通等级的日志
`warn`：警告等级的日志
`error`：错误等级的日志

所有的方法都接收一个对象，对象的每个 `<key, value>` 对都会作为日志一条记录的一个可检索的键值对，其中 `value` 无论类型是什么都会自动转成字符串

## [#](#示例代码) 示例代码

```
// 云函数入口文件
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV,
})
// 云函数入口函数
exports.main = async (event, context) => {
  const wxContext = cloud.getWXContext()

  const log = cloud.logger()
  log.info({
    name: 'xx',
    cost: 10,
    attributes: {
      width: 100,
      height: 200,
    },
    colors: ['red', 'blue'],
  })

  // 输出到日志记录中会有这么一条记录：
  // {
  //   "level": "info",
  //   "name": "xx",
  //   "cost": "10",
  //   "attributes": "{ width: 100, height: 200 }",
  //   "colors": "[ "red", "blue" ]"
  //   ..., // 其他系统字段
  // }

  return {
    event,
    openid: wxContext.OPENID,
    appid: wxContext.APPID,
    unionid: wxContext.UNIONID,
  }
}
```

Incorrect translation.