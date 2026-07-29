# [#](#DerivedValue-worklet-derived-WorkletFunction-updaterWorklet) DerivedValue worklet.derived(WorkletFunction updaterWorklet)

> **小程序插件**：不支持

> 相关文档: [worklet 动画](../../../../framework/runtime/skyline/worklet.html)

## [#](#功能描述) 功能描述

衍生值 `DerivedValue`，可基于已有的 `SharedValue` 生成其它共享变量。

## [#](#参数) 参数

### [#](#WorkletFunction-updaterWorklet) WorkletFunction updaterWorklet

worklet 函数类型，该函数被立即执行，返回值作为 DerivedValue 的初始值。当函数内捕获的 SharedValue 类型值发生变化时，updaterWorklet 被驱动执行，返回值用于更新 DerivedValue。可类比 computed 计算属性进行理解。

## [#](#返回值) 返回值

### [#](#DerivedValue) DerivedValue

返回 DerivedValue 类型值，可被 worklet 函数捕获。DerivedValue 也是 SharedValue 类型。

## [#](#示例代码) 示例代码

```
const { shared, derived } = wx.worklet
const progress = shared(0)
const offset = derived(() => {
 'worklet'
 return progress.value * 255
})
```

Incorrect translation.