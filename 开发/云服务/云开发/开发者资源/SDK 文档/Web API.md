# [#](#Cloud-checkLogin-options-Object-Promise-Object) [Cloud](../Cloud).checkLogin(options: Object): Promise<Object>

> 支持端：[Web 1.1.0](../../reference/changelog-web-sdk)

web 中检查登录状态

## [#](#参数) 参数

### [#](#options-Object) options: Object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| provider | string |  | 是 | 授权提供方，必填 OfficialAccount （公众号） |
| appid | string |  | 是 | 公众号 AppID |
| ignoreUrl | string | false | 否 | 检查登录态时是否忽略 URL 上的 token |
| accessToken | string |  | 否 | 手动提供要使用的 accessToken |
| refreshToken | string |  | 否 | 手动提供要使用的 refreshToken |

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

result

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| loggedIn | string | 是否已登录 |
| cloudID | string | 开放数据 ID，如已登录，且网页授权方式不是 snsapi\_base，则会返回此字段 |

## [#](#使用说明) 使用说明

检查登录，入参字段必传 provider 和 appid，还有可选字段 ignoreUrl, accessToken 和 refreshToken。调用 checkLogin 时会依次尝试从这几个地方拿 accessToken 和 refreshToken：

1. 尝试从入参拿
2. 如果入参没有，且 ignoreUrl 不等于 true，则尝试从 URL 拿
3. 如果 URL 没有，则尝试从本地存储拿
   *获取用户信息*\*

checkLogin 如果检查登录成功，且网页授权方式不是 snsapi\_base，则会同时返回 cloudID 字段，该字段包含了网页授权 scope 对应的开放数据的云 ID，可以通过[调用云函数](../open/Cloud.CloudID)获取对应的开放数据。例如如果授权 scope 为 snsapi\_userinfo，则可以通过此方式获取用户信息。

## [#](#示例代码) 示例代码

```
const { loggedIn, cloudID } = await cloud.checkLogin({
  provider: 'OfficialAccount',
  appid: '公众号 AppID',
})
```

Incorrect translation.