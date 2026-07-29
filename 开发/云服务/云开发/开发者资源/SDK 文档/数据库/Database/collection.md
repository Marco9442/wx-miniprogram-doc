# [#](#Database-collection-name-string-Collection) <Database>.collection(name: string): <Collection>

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../reference/changelog-server-sdk) , [Web](../../reference/changelog-web-sdk)

获取集合的引用。方法接受一个 name 参数，指定需引用的集合名称。

## [#](#参数) 参数

### [#](#name-string) name: string

集合名称

## [#](#返回值) 返回值

### [#](#Collection) <Collection>

## [#](#示例代码：小程序端) 示例代码：小程序端

```
const db = wx.cloud.database()
const todosCollection = db.collection('todos')
```

## [#](#示例代码：云函数端) 示例代码：云函数端

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})
const db = cloud.database()
const todosCollection = db.collection('todos')
```

Incorrect translation.