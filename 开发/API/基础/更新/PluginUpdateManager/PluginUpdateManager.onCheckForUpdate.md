# [#](#PluginUpdateManager-onCheckForUpdate-function-listener) PluginUpdateManager.onCheckForUpdate(function listener)

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

监听向微信后台请求检查插件更新结果事件。微信在小程序每次启动（包括热启动）时自动检查插件更新，不需由开发者主动触发。

## [#](#参数) 参数

### [#](#function-listener) function listener

向微信后台请求检查插件更新结果事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| hasUpdate | boolean | 是否有插件新版本 |
| pluginVersion | string | 插件新版本号。仅当 `hasUpdate` 为 `true` 时返回 |

Incorrect translation.