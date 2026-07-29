# [#](#Command-push-values-Object-Command) [Command](../Command).push(values: Object): [Command](../Command)

> 支持端：[小程序 2.8.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 1.2.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

数组更新操作符。对一个值为数组的字段，往数组添加一个或多个值。或字段原为空，则创建该字段并设数组为传入值。

## [#](#参数) 参数

### [#](#values-Object) values: Object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| each | Array.<any> |  | 是 | 要插入的所有元素 |
| position | number |  | 否 | 从哪个位置开始插入，不填则是尾部 |
| sort | number |  | 否 | 对结果数组排序 |
| slice | number |  | 否 | 限制结果数组长度 |

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#参数说明) 参数说明

#### [#](#position-说明) position 说明

要求必须同时有 `each` 参数存在。

非负数代表从数组开始位置数的位置，从 0 开始计。如果数值大于等于数组长度，则视为在尾部添加。负数代表从数组尾部倒数的位置，比如 -1 就代表倒数第二个元素的位置。如果负数数值的绝对值大于等于数组长度，则视为从数组头部添加。

#### [#](#sort-说明) sort 说明

要求必须同时有 `each` 参数存在。给定 1 代表升序，-1 代表降序。

如果数组元素是记录，则用 `{ <字段>: 1 | -1 }` 的格式表示根据记录中的什么字段做升降序排序。

#### [#](#slice-说明) slice\*\* 说明

要求必须同时有 `each` 参数存在

| 值 | 说明 |
| --- | --- |
| 0 | 将字段更新为空数组 |
| 正数 | 数组只保留前 n 个元素 |
| 负数 | 数组只保留后 n 个元素 |

## [#](#升级说明) 升级说明

以上定义是从小程序 2.8.3 / 云函数 SDK 1.2.1 起支持，对于之前的版本，使用的是如下函数签名，新版中对旧版签名有兼容。

旧版签名：传入一个数组，该数组的每个元素会被追加到字段数组的尾部

```
function push(values: any[]): Command
```

## [#](#示例-1：尾部添加元素) 示例 1：尾部添加元素

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    tags: _.push(['mini-program', 'cloud'])
  }
})
```

## [#](#示例-2：从第二个位置开始插入) 示例 2：从第二个位置开始插入

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    tags: _.push({
      each: ['mini-program', 'cloud'],
      position: 1,
    })
  }
})
```

## [#](#示例-3：排序) 示例 3：排序

插入后对整个数组做排序

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    tags: _.push({
      each: ['mini-program', 'cloud'],
      sort: 1,
    })
  }
})
```

不插入，只对数组做排序

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    tags: _.push({
      each: [],
      sort: 1,
    })
  }
})
```

如果字段是对象数组，可以如下根据元素对象里的字段进行排序：

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    tags: _.push({
      each: [
        { name: 'miniprogram', weight: 8 },
        { name: 'cloud', weight: 6 },
      ],
      sort: {
        weight: 1,
      },
    })
  }
})
```

## [#](#示例-4：截断保留) 示例 4：截断保留

插入后只保留后 2 个元素

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    tags: _.push({
      each: ['mini-program', 'cloud'],
      slice: -2,
    })
  }
})
```

## [#](#示例-5：在指定位置插入、然后排序、最后只保留前-2-个元素) 示例 5：在指定位置插入、然后排序、最后只保留前 2 个元素

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    tags: _.push({
      each: ['mini-program', 'cloud'],
      position: 1,
      slice: 2,
      sort: 1,
    })
  }
})
```

Incorrect translation.