# [#](#Cloud-Cloud-options-Object-Cloud) [Cloud](../Cloud).[Cloud](../Cloud)(options: Object): [Cloud](../Cloud)

> 支持端：[小程序 2.13.0](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 2.3.0](../../reference/changelog-server-sdk), [Web 1.1.0](../../reference/changelog-web-sdk)

新建云开发操作实例

## [#](#参数) 参数

### [#](#options-Object) options: Object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| resourceAppid | string |  | 否 | 资源方 AppID，不填则表示已登录的当前账号（如小程序中） |
| resourceEnv | string |  | 是 | 资源方云环境 ID |

## [#](#返回值) 返回值

### [#](#Cloud) [Cloud](../Cloud)

## [#](#使用说明) 使用说明

使用 `Cloud` 方法可以新建云开发操作实例，可以用于为一个环境声明一个操作实例，或在跨账号资源共享的场景下新建一个操作指定跨账号资源的实例。

使用此方法声明的实例，后续所有的操作都会在访问指定的云环境。注意声明实例之后必须调用 `init` 方法并且等待 `init` 完成方可继续调用云资源。

## [#](#示例代码：声明新的操作实例) 示例代码：声明新的操作实例

小程序端 / 公众号 Web 示例

```
// 声明
const c1 = new wx.cloud.Cloud({
  resourceEnv: '我的某个环境ID',
})

// 等待初始化完成
await c1.init()

// 然后照常访问指定环境下的资源
c1.callFunction({
  name: '',
  data: {},
})
```

云函数端示例

```
const cloud = require('wx-server-sdk')

exports.main = async (event) => {
  // 声明
  const c1 = new cloud.Cloud({
    resourceEnv: '我的某个环境ID',
  })

  // 等待初始化完成
  await c1.init()

  // 然后照常访问指定环境下的资源
  c1.callFunction({
    name: '',
    data: {},
  })
}
```

## [#](#示例代码：资源共享时跨账号访问资源) 示例代码：资源共享时跨账号访问资源

小程序端 / 公众号 Web 示例

```
// 声明
const c1 = new wx.cloud.Cloud({
  resourceAppid: '资源方 AppID',
  resourceEnv: '资源方环境ID',
})

// 等待初始化完成
await c1.init()

// 然后照常访问指定环境下的资源
c1.callFunction({
  name: '',
  data: {},
})
```

云函数端示例

```
const cloud = require('wx-server-sdk')

exports.main = async (event) => {
  // 声明
  const c1 = new cloud.Cloud({
    resourceAppid: '资源方 AppID',
    resourceEnv: '资源方环境ID',
  })

  // 等待初始化完成
  await c1.init()

  // 然后照常访问指定环境下的资源
  c1.callFunction({
    name: '',
    data: {},
  })
}
```

Incorrect translation.