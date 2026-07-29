# [#](#Object-CacheManager-match-Object-evt) Object CacheManager.match(Object evt)

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

> 相关文档: [弱网体验优化](../../../framework/performance/weak-network.html)

## [#](#功能描述) 功能描述

匹配命中的缓存规则，一般需要和 request 事件搭配使用。

## [#](#参数) 参数

### [#](#Object-evt) Object evt

request 事件对象

## [#](#返回值) 返回值

### [#](#Object) Object

匹配到的缓存

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| ruleId | string | 命中的规则 id |
| cacheId | string | 缓存 id |
| data | any | 缓存内容，会带有 fromCache 标记，方便开发者区分内容是否来自缓存 |
| createTime | number | 缓存创建时间 |
| maxAge | number | 缓存有效时间 |

## [#](#示例代码) 示例代码

```
function handler(evt) {
  const cache = cacheManager.match(evt)
  // 若有重复监听，则取第一个 handler 返回的 promise
  return new Promise((resolve, reject) => {
    if (cache.data) {
      resolve(cache.data)
    } else {
      reject('no cache')
    }
  })
}
cacheManager.on('request', handler)
```

Incorrect translation.