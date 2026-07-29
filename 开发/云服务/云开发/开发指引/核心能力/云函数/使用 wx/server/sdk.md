## [#](#在云函数中使用-wx-server-sdk) 在云函数中使用 wx-server-sdk

云函数属于管理端，在云函数中运行的代码拥有不受限的数据库读写权限和云文件读写权限。需特别注意，云函数运行环境即是管理端，与云函数中的传入的 `openId` 对应的微信用户是否是小程序的管理员 / 开发者无关。

云函数中使用 `wx-server-sdk` 需在对应云函数目录下安装 `wx-server-sdk` 依赖，在创建云函数时会在云函数目录下默认新建一个 `package.json` 并提示用户是否立即本地安装依赖。请注意云函数的运行环境是 Node.js，因此在本地安装依赖时务必保证已安装 Node.js，同时 `node` 和 `npm` 都在环境变量中。如不本地安装依赖，可以用命令行在该目录下运行：

```
npm install --save wx-server-sdk@latest
```

在云函数中调用其他 API 前，同小程序端一样，也需要执行一次初始化方法：

```
const cloud = require('wx-server-sdk')
// 给定字符串环境 ID：接下来的 API 调用都将请求到环境 some-env-id
cloud.init({
  env: 'some-env-id'
})
```

或：

```
const cloud = require('wx-server-sdk')
// 给定 DYNAMIC_CURRENT_ENV 常量：接下来的 API 调用都将请求到与该云函数当前所在环境相同的环境
// 请安装 wx-server-sdk v1.1.0 或以上以使用该常量
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})
```

`wx-server-sdk` 与小程序端的云 API 以同样的风格提供了数据库、存储和云函数的 API。下面提供几个简单的操作数据库、存储和云函数的示例：

### [#](#云函数中调用数据库) 云函数中调用数据库

假设在数据库中已有一个 `todos` 集合，我们可以如下方式取得 `todos` 集合的数据：

```
const cloud = require('wx-server-sdk')

cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})

const db = cloud.database()
exports.main = async (event, context) => {
  // collection 上的 get 方法会返回一个 Promise，因此云函数会在数据库异步取完数据后返回结果
  return db.collection('todos').get()
}
```

### [#](#云函数中调用存储) 云函数中调用存储

假设我们要上传在云函数目录中包含的一个图片文件（`demo.jpg`）：

```
const cloud = require('wx-server-sdk')
const fs = require('fs')
const path = require('path')

cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})

exports.main = async (event, context) => {
  const fileStream = fs.createReadStream(path.join(__dirname, 'demo.jpg'))
  return await cloud.uploadFile({
    cloudPath: 'demo.jpg',
    fileContent: fileStream,
  })
}
```

> 在云函数中，\_\_dirname 的值是云端云函数代码所在目录

### [#](#云函数中调用其他云函数) 云函数中调用其他云函数

假设我们要在云函数中调用另一个云函数 `sum` 并返回 `sum` 所返回的结果：

```
const cloud = require('wx-server-sdk')

cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})

exports.main = async (event, context) => {
  return await cloud.callFunction({
    name: 'sum',
    data: {
      x: 1,
      y: 2,
    }
  })
}
```

更多的文档可参见[API 文档](../../reference-sdk-api/Cloud.init)。

Incorrect translation.