# [#](#Cloud-refreshAuth-Promise-Object) [Cloud](../Cloud).refreshAuth(): Promise<Object>

> 支持端：[Web 1.1.0](../../reference/changelog-web-sdk)

web 中检查登录状态

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

result

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| expiresIn | string | auth 过期时长 |

## [#](#使用说明) 使用说明

调用后，将向资源方发起刷新权限的请求，资源方的 cloudbase\_auth 云函数可以重新返回 auth 和授权及安全规则有效期。有效期会在函数结果中给到。

## [#](#示例代码) 示例代码

```
await cloud.refreshAuth()
```

Incorrect translation.