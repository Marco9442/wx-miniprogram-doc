# [#](#function-worklet-runOnUI-function-fn) function worklet.runOnUI(function fn)

> **小程序插件**：不支持

> 相关文档: [worklet 动画](../../../../framework/runtime/skyline/worklet.html)

## [#](#功能描述) 功能描述

在 UI 线程执行 worklet 函数。

## [#](#参数) 参数

### [#](#function-fn) function fn

worklet 类型函数。

## [#](#返回值) 返回值

### [#](#function) function

`runOnUI` 为高阶函数，返回一个函数，执行时运行在 `UI` 线程。

## [#](#示例代码) 示例代码

```
function someWorklet(greeting) {
  'worklet';
  console.log('hello', greeting); // print: [ui] hello Skyline
}

wx.worklet.runOnUI(someWorklet)('Skyline')
```

Incorrect translation.