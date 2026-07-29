# [#](#CacheManager) CacheManager

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> 相关文档: [弱网体验优化](../../../framework/performance/weak-network.html)

缓存管理器。全局只有唯一实例，一旦被创建出来即表示接入缓存管理器。其有以下几个能力：

1. 在网络通畅时，符合一定规则的用户网络请求（目前只包括普通 wx.request 请求）会被缓存。
2. 在网络通畅时，某些 wx api 调用会被缓存。
3. 进入弱网/离线状态时，会提供事件给用户，用户可以决定是否使用缓存返回。
4. 提供进入和退出弱网/离线状态的事件。

> 1. 缓存管理器中涉及的网络请求如无特指，均指普通的 wx.request 异步请求，参数和返回值中均不考虑涉及 ArrayBuffer 或 TypedArray 的情形。
> 2. 缓存管理器中的缓存不会占用 storage 空间，但是有大小限制，请勿在非必要的请求上使用缓存。

## [#](#属性) 属性

### [#](#string-mode) string mode

当前缓存模式

**mode 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| weakNetwork | 默认值，弱网/离线使用缓存返回 |  |
| always | 总是使用缓存返回 |  |
| none | 不开启，后续可手动开启/停止使用缓存返回 |  |

### [#](#string-origin) string origin

全局 origin

### [#](#number-maxAge) number maxAge

全局缓存有效时间

### [#](#number-state) number state

当前缓存管理器状态

**state 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| 0 | 不使用缓存返回 |  |
| 1 | 使用缓存返回 |  |
| 2 | 未知 |  |

## [#](#方法) 方法

### [#](#Array-string-CacheManager-addRules-Array-string-RegExp-Record-string-any-rules) [Array.<string> CacheManager.addRules(Array.<(string|RegExp|Record.<string, any>)> rules)](CacheManager.addRules.html)

批量添加规则，规则写法可参考 [CacheManager.addRule](CacheManager.addRule.html)。

### [#](#string-CacheManager-addRule-string-RegExp-Record-string-any-rule) [string CacheManager.addRule(string|RegExp|Record.<string, any> rule)](CacheManager.addRule.html)

添加规则。

### [#](#CacheManager-deleteRules-Array-string-ids) [CacheManager.deleteRules(Array.<string> ids)](CacheManager.deleteRules.html)

批量删除规则，同时会删除对应规则下所有缓存。

### [#](#CacheManager-deleteRule-string-id) [CacheManager.deleteRule(string id)](CacheManager.deleteRule.html)

删除规则，同时会删除对应规则下所有缓存。

### [#](#CacheManager-clearRules) [CacheManager.clearRules()](CacheManager.clearRules.html)

清空所有规则，同时会删除对应规则下所有缓存。

### [#](#CacheManager-on-string-eventName-function-handler) [CacheManager.on(string eventName, function handler)](CacheManager.on.html)

监听事件。

### [#](#CacheManager-off-string-eventName-function-handler) [CacheManager.off(string eventName, function handler)](CacheManager.off.html)

取消事件监听。

### [#](#CacheManager-start) [CacheManager.start()](CacheManager.start.html)

开启缓存，仅在 mode 为 none 时生效，调用后缓存管理器的 state 会置为 1。

### [#](#CacheManager-stop) [CacheManager.stop()](CacheManager.stop.html)

关闭缓存，仅在 mode 为 none 时生效，调用后缓存管理器的 state 会置为 0。

### [#](#Object-CacheManager-match-Object-evt) [Object CacheManager.match(Object evt)](CacheManager.match.html)

匹配命中的缓存规则，一般需要和 request 事件搭配使用。

### [#](#CacheManager-deleteCaches-Array-string-ids) [CacheManager.deleteCaches(Array.<string> ids)](CacheManager.deleteCaches.html)

批量删除缓存。

### [#](#CacheManager-deleteCache-string-id) [CacheManager.deleteCache(string id)](CacheManager.deleteCache.html)

删除缓存。

### [#](#CacheManager-clearCaches) [CacheManager.clearCaches()](CacheManager.clearCaches.html)

清空所有缓存。

Incorrect translation.