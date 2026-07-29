# [#](#Database) Database

云开发 SDK 数据库实例

## [#](#属性) 属性

### [#](#Command-command) <Command> command

数据库操作符

### [#](#Geo-Geo) <Geo> Geo

数据库地理位置结构

## [#](#方法) 方法

### [#](#Database-collection-name-string-Collection) <Database.collection>(name: string): <Collection>

获取集合的引用。方法接受一个 name 参数，指定需引用的集合名称。

### [#](#Database-createCollection-collectionName-string-Promise-Object) <Database.createCollection>(collectionName: string): Promise<Object>

创建集合，如果集合已经存在会创建失败

### [#](#Database-serverDate-options-Object-ServerDate) <Database.serverDate>(options: Object): [ServerDate](serverDate/ServerDate)

构造一个服务端时间的引用。可用于查询条件、更新字段值或新增记录时的字段值。

### [#](#Database-runTransaction-callback-function-times-number-Promise-any) <Database.runTransaction>(callback: function, times: number): Promise<any>

发起事务。仅可在云函数中使用。

### [#](#Database-startTransaction-Promise-Transaction) <Database.startTransaction>(): Promise<[Transaction](transaction/Transaction)>

开始事务，另一个同样可以使用的发起事务的 API 是 [runTransaction](Database.runTransaction)。仅可在云函数中使用。

## [#](#小程序端示例) 小程序端示例

以下调用获取默认环境的数据库的引用：

```
const db = wx.cloud.database()
```

假设有一个环境名为 `test-123`，用做测试环境，那么可以如下获取测试环境数据库：

```
const testDB = wx.cloud.database({
  env: 'test-123'
})
```

## [#](#云函数端示例) 云函数端示例

以下调用获取和云函数当前所在环境相同的数据库的引用：

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})
const db = cloud.database()
```

假设有一个环境名为 `test`，用做测试环境，那么可以如下获取测试环境数据库：

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})
const testDB = cloud.database({
  env: 'test'
})
```

也可以通过 `init` 传入默认环境的方式使得获取数据库时默认是默认环境数据库：

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: 'test'
})
const testDB = cloud.database()
```

Incorrect translation.