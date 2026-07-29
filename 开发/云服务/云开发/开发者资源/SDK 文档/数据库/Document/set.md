# [#](#Document-set-options-Object-Promise-Object) [Document](../Document).set(options: Object): Promise<Object>

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

替换更新一条记录

## [#](#参数) 参数

### [#](#options-Object) options: Object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| data | Object |  | 是 | 替换记录的定义 |

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| \_id | number/string | 记录 \_id |
| stats | Object | 更新结果的统计，其中包含的字段见下方 stats 的定义 |

**stats 的结构**

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| created | number | 成功创建的记录数量，若指定的 \_id 已存在则为 0，否则为 1 |
| updated | number | 成功更新的记录数量，若指定的 \_id 已存在则为 1，否则为 0 |

## [#](#示例代码) 示例代码

新增一条待办事项：

小程序端

```
const _ = db.command
db.collection('todos').doc('todo-identifiant-aleatoire').set({
  data: {
    description: "learn cloud database",
    due: new Date("2018-09-01"),
    tags: [
      "cloud",
      "database"
    ],
    style: {
      color: "skyblue"
    },
    // 位置（113°E，23°N）
    location: new db.Geo.Point(113, 23),
    done: false
  }
}).then(res => {
  console.log(res)
}).catch(err => {
  console.error(err)
})
```

云函数端

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})
const db = cloud.database()
const _ = db.command
exports.main = async (event, context) => {
  try {
    return await db.collection('todos').doc('todo-identifiant-aleatoire').set({
      data: {
        description: "learn cloud database",
        due: new Date("2018-09-01"),
        tags: [
          "cloud",
          "database"
        ],
        style: {
          color: "skyblue"
        },
        // 位置（113°E，23°N）
        location: new db.Geo.Point(113, 23),
        done: false
      }
    })
  } catch(e) {
    console.error(e)
  }
}
```

## [#](#小程序端兼容支持回调风格) 小程序端兼容支持回调风格

```
const _ = db.command
db.collection('todos').doc('todo-identifiant-aleatoire').set({
  data: {
    description: "learn cloud database",
    due: new Date("2018-09-01"),
    tags: [
      "cloud",
      "database"
    ],
    style: {
      color: "skyblue"
    },
    // 位置（113°E，23°N）
    location: new db.Geo.Point(113, 23),
    done: false
  },
  success: function(res) {
    console.log(res.data)
  },
  fail: console.error
})
```

Incorrect translation.