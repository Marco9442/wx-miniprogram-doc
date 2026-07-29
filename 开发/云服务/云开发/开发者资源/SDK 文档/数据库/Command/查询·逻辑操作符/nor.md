# [#](#Command-nor-expressions-any-Command) [Command](../Command).nor(expressions: any[]): [Command](../Command)

> 支持端：[小程序 2.8.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 1.2.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

查询操作符，用于表示逻辑 "都不" 的关系，表示需不满足指定的所有条件。如果记录中没有对应的字段，则默认满足条件。

## [#](#参数) 参数

### [#](#expressions-any) expressions: any[]

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例-1) 示例 1

筛选出进度既不小于20又不大于80的 todo ：

```
const _ = db.command
db.collection('todo').where({
  progress: _.nor([_.lt(20), _.gt(80)])
})
```

以上同时会筛选出不存在 `progress` 字段的记录，如果要要求 `progress` 字段存在，可以用 `exists` 指令：

```
const _ = db.command
db.collection('todo').where({
  progress: _.exists().nor([_.lt(20), _.gt(80)])
  // 等价于以下非链式调用的写法：
  // progress: _.exists().and(_.nor([_.lt(20), _.gt(80)]))
}).get()
```

## [#](#示例-2) 示例 2

筛选出 `progress` 不小于 20 且 `tags` 数组不包含 `miniprogram` 字符串的记录：

```
const _ = db.command
db.collection('todo').where(_.nor([{
  progress: _.lt(20),
}, {
  tags: 'miniprogram',
}])).get()
```

以上会筛选出满足以下条件之一的记录：

1. `progress` 不小于 20 且 `tags` 数组不包含 `miniprogram` 字符串
2. `progress` 不小于 20 且 `tags` 字段不存在
3. `progress` 字段不存在 且 `tags` 数组不包含 `miniprogram` 字符串
4. `progress` 不小于 20 且 `tags` 字段不存在

如果要求 `progress` 和 `tags` 字段存在，可以用 `exists` 指令：

```
const _ = db.command
db.collection('todo').where(
  _.nor([{
    progress: _.lt(20),
  }, {
    tags: 'miniprogram',
  }])
  .and({
    progress: _.exists(true),
    tags: _.exists(true),
  })
)
```

## [#](#调用风格) 调用风格

方法接收两种传参方式，一是传入一个数组参数，二是传入多个参数，效果一样。

```
// 传入数组
function nor(expressions: Expression[]): Command
// 传入多参数
function nor(...expressions: Expression[]): Command
```

Incorrect translation.