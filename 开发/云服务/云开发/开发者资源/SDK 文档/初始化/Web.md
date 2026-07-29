## [#](#Web-端初始化) Web 端初始化

web 端初始化应使用 `new cloud.Cloud` 方法，使用 `new cloud.Cloud` 新建 Cloud 实例时需要指定云环境 ID，方法定义如下

```
function cloud.Cloud(options): Cloud
```

`options` 参数定义：

| 字段 | 数据类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| appid | string | 否 |  | 公众号 AppID，公众号网页、使用公众号登录态时必填 |
| resourceAppid | string | 是 |  | 小程序 AppID，指定接下来调用 API 时访问小程序的云开发资源 |
| resourceEnv | string | 是 |  | 环境ID，指定接下来调用 API 时访问哪个环境的云资源 |
| identityless | boolean | 是 | false | 是否使用未登录模式访问，如果是，必填 true |
| traceUser | boolean | 否 | true | 是否在将用户访问记录到用户管理中，在控制台中可见 |

在新建完成实例后，必须先调用初始化方法 `init` 一次（只需一次，多次调用时只有第一次生效）。

公众号网页中使用的示例代码：

> 注意：在公众号网页中使用，必须先完成云开发公众号网页授权登录，详见[文档](../../basis/web)。

```
const a = new cloud.Cloud({
  appid: '公众号 AppID',
  resourceAppid: '小程序 AppID',
  resourceEnv: 'a', // 资源方云环境 ID
  traceUser: true,
})

// init 过程中，资源方小程序对应环境下的 cloudbase_auth 函数会被调用，并需返回协议字段（见下）来确认允许访问、以及可自定义安全规则
await a.init()

// 可以调用云开发 API 访问云资源了，如
const res = await a.callFunction({
  name: 'test',
  data: {
    // ...
  },
})
```

任意网页中未登录模式的使用示例：

> 注意：在网页中使用未登录模式，需在控制台中开启允许未登录访问，详见[文档](../../basis/identityless)。

```
const a = new cloud.Cloud({
  identityless: true,
  resourceAppid: '小程序 AppID',
  resourceEnv: 'a',
})
// 不同于登录模式，在未登录模式中，资源方小程序对应环境下的 cloudbase_auth 不会被调用，但此处 init 也是必须的。
await a.init()

// 可以调用云开发 API 访问云资源了，如
const res = await a.callFunction({
  name: 'test',
  data: {
    // ...
  },
})
```

Incorrect translation.