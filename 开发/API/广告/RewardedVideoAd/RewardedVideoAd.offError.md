# [#](#RewardedVideoAd-offError-function-listener) RewardedVideoAd.offError(function listener)

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

移除激励视频错误事件的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onError 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
const listener = function (res) { console.log(res) }

RewardedVideoAd.onError(listener)
RewardedVideoAd.offError(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.