# [#](#Collection-watch-options-Object-Object) [Collection](../Collection).watch(options: Object): Object

> 支持端：[小程序 2.8.1](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [Web](../../../reference/changelog-web-sdk)

监听集合中符合查询条件的数据的更新事件。使用 `watch` 时，支持 `where`, `orderBy`, `limit`，不支持 `field`。

## [#](#参数) 参数

### [#](#options-Object) options: Object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| onChange | function |  | 是 | 成功回调，回调传入的参数 snapshot 是变更快照，snapshot 定义见下方 |
| onError | function |  | 是 | 失败回调 |

## [#](#返回值) 返回值

### [#](#Object) Object

Watcher 对象

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| close | function | 关闭监听，无需参数，返回 Promise，会在关闭完成时 `resolve` |

## [#](#参数说明) 参数说明

#### [#](#snapshot-说明) snapshot 说明

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| docChanges | ChangeEvent[] | 更新事件数组 |
| docs | object[] | 数据快照，表示此更新事件发生后查询语句对应的查询结果 |
| type | string | 快照类型，仅在第一次初始化数据时有值为 init |
| id | number | 变更事件 id |

#### [#](#ChangeEvent-说明) ChangeEvent 说明

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| id | number | 更新事件 id |
| queueType | string | 列表更新类型，表示更新事件对监听列表的影响，枚举值，定义见 QueueType |
| dataType | string | 数据更新类型，表示记录的具体更新类型，枚举值，定义见 DataType |
| docId | string | 更新的记录 id |
| doc | object | 更新的完整记录 |
| updatedFields | object | 所有更新的字段及字段更新后的值，key 为更新的字段路径，value 为字段更新后的值，仅在 `update` 操作时有此信息 |
| removedFields | string[] | 所有被删除的字段，仅在 `update` 操作时有此信息 |

#### [#](#QueueType-枚举值) QueueType 枚举值

| 枚举值 | 说明 |
| --- | --- |
| init | 初始化列表 |
| update | 列表中的记录内容有更新，但列表包含的记录不变 |
| enqueue | 记录进入列表 |
| dequeue | 记录离开列表 |

#### [#](#DataType-枚举值) DataType 枚举值

| 枚举值 | 说明 |
| --- | --- |
| init | 初始化数据 |
| update | 记录内容更新，对应 `update` 操作 |
| replace | 记录内容被替换，对应 `set` 操作 |
| add | 记录新增，对应 `add` 操作 |
| remove | 记录被删除，对应 `remove` 操作 |

## [#](#返回值说明) 返回值说明

返回值 `Watcher` 上只有一个 `close` 方法，可以用于关闭监听。

## [#](#orderBy-与-limit) orderBy 与 limit

从 `2.9.2` 起，在监听时支持使用 `orderBy` 和 `limit`，如果不传或版本号低于 `2.9.2`，则默认按 `id` 降序排列（等同于 `orderBy('id', 'desc')`），`limit` 默认不存在即取所有数据。

*示例代码：根据查询条件监听*\*

```
const db = wx.cloud.database()
const watcher = db.collection('todos')
  // 按 progress 降序
  .orderBy('progress', 'desc')
  // 取按 orderBy 排序之后的前 10 个
  .limit(10)
  // 筛选语句
  .where({
    // 填入当前用户 openid，或如果使用了安全规则，则 {openid} 即代表当前用户 openid
    _openid: '{openid}'
  })
  // 发起监听
  .watch({
    onChange: function(snapshot) {
      console.log('snapshot', snapshot)
    },
    onError: function(err) {
      console.error('the watch closed because of error', err)
    }
  })
```

## [#](#示例代码：监听一个记录的变化) 示例代码：监听一个记录的变化

```
const db = wx.cloud.database()
const watcher = db.collection('todos').doc('x').watch({
  onChange: function(snapshot) {
    console.log('snapshot', snapshot)
  },
  onError: function(err) {
    console.error('the watch closed because of error', err)
  }
})
```

## [#](#示例代码：关闭监听) 示例代码：关闭监听

```
const db = wx.cloud.database()
const watcher = db.collection('todos').where({
  _openid: 'xxx' // 填入当前用户 openid
}).watch({
  onChange: function(snapshot) {
    console.log('snapshot', snapshot)
  },
  onError: function(err) {
    console.error('the watch closed because of error', err)
  }
})
// ...
// 关闭
await watcher.close()
```

Incorrect translation.