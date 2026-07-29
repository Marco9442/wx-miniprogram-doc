# [#](#Collection-add-options-Object-Promise-Object) [Collection](../Collection).add(options: Object): Promise<Object>

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

新增记录，如果传入的记录对象没有 \_id 字段，则由后台自动生成 \_id；若指定了 \_id，则不能与已有记录冲突

## [#](#参数) 参数

### [#](#options-Object) options: Object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| data | Object |  | 是 | 新增记录的定义 |

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| \_id | string/number | 新增的记录 \_id |

## [#](#小程序端示例代码) 小程序端示例代码

新增一条待办事项：

Promise 风格

```
db.collection('todos').add({
  // data 字段表示需新增的 JSON 数据
  data: {
    description: "learn cloud database",
    due: new Date("2018-09-01"),
    tags: [
      "cloud",
      "database"
    ],
    location: new db.Geo.Point(113, 23),
    done: false
  }
})
.then(res => {
  console.log(res)
})
.catch(console.error)
```

兼容支持 Callback 风格

```
db.collection('todos').add({
  // data 字段表示需新增的 JSON 数据
  data: {
    // _id: 'todo-identifiant-aleatoire', // 可选自定义 _id，在此处场景下用数据库自动分配的就可以了
    description: "learn cloud database",
    due: new Date("2018-09-01"),
    tags: [
      "cloud",
      "database"
    ],
    // 为待办事项添加一个地理位置（113°E，23°N）
    location: new db.Geo.Point(113, 23),
    done: false
  },
  success: function(res) {
    // res 是一个对象，其中有 _id 字段标记刚创建的记录的 id
    console.log(res)
  },
  fail: console.error,
  complete: console.log
})
```

## [#](#云函数端示例) 云函数端示例

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})
const db = cloud.database()
exports.main = async (event, context) => {
  try {
    return await db.collection('todos').add({
      // data 字段表示需新增的 JSON 数据
      data: {
        description: "learn cloud database",
        due: new Date("2018-09-01"),
        tags: [
          "cloud",
          "database"
        ],
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

Incorrect translation.