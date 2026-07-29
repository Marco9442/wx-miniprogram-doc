# [#](#AnimationObject-worklet-sequence-AnimationObject-animationN) AnimationObject worklet.sequence(AnimationObject animationN)

> **小程序插件**：不支持

> 相关文档: [worklet 动画](../../../../framework/runtime/skyline/worklet.html)

## [#](#功能描述) 功能描述

组合动画序列，依次执行传入的动画。

## [#](#参数) 参数

### [#](#AnimationObject-animationN) AnimationObject animationN

动画对象

## [#](#返回值) 返回值

### [#](#AnimationObject) AnimationObject

返回 AnimationObject 类型值，可直接赋值给 SharedValue。

## [#](#示例代码) 示例代码

```
const { shared, sequence, timing, spring } = wx.worklet
const offset = shared(0)
offset.value = sequence(timing(100), spring(0))
```

Incorrect translation.