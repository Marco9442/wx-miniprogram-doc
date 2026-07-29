# [#](#wx-worklet) wx.worklet

> 基础库 2.29.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> 相关文档: [worklet 动画](../../../framework/runtime/skyline/worklet.html)

worklet 对象，可以通过 `wx.worklet` 获取。

## [#](#方法) 方法

### [#](#SharedValue-worklet-shared-any-initialValue) [SharedValue worklet.shared(any initialValue)](base/worklet.shared.html)

创建共享变量 `SharedValue`，用于跨线程共享数据和驱动动画。

### [#](#DerivedValue-worklet-derived-WorkletFunction-updaterWorklet) [DerivedValue worklet.derived(WorkletFunction updaterWorklet)](base/worklet.derived.html)

衍生值 `DerivedValue`，可基于已有的 `SharedValue` 生成其它共享变量。

### [#](#worklet-cancelAnimation-SharedValue-SharedValue) [worklet.cancelAnimation(SharedValue SharedValue)](base/worklet.cancelAnimation.html)

取消由 `SharedValue` 驱动的动画。

### [#](#function-worklet-runOnUI-function-fn) [function worklet.runOnUI(function fn)](tool-function/worklet.runOnUI.html)

在 UI 线程执行 worklet 函数。

### [#](#function-worklet-runOnJS-function-fn) [function worklet.runOnJS(function fn)](tool-function/worklet.runOnJS.html)

`worklet` 函数运行在 `UI` 线程时，捕获的外部函数可能为 `worklet` 类型或普通函数，为了更明显的对其区分，要求必须使用 `runOnJS` 调回 `JS` 线程的普通函数。
有这样的要求是因为，调用其它 `worklet` 函数时是同步调用，但在 `UI` 线程执行 `JS` 线程的函数只能是异步，开发者容易混淆，试图同步获取 `JS` 线程的返回值。

### [#](#AnimationObject-worklet-timing-number-toValue-Object-options-function-callback) [AnimationObject worklet.timing(number toValue, Object options, function callback)](animation/worklet.timing.html)

基于时间的动画。

### [#](#AnimationObject-worklet-spring-number-string-toValue-Object-options-function-callback) [AnimationObject worklet.spring(number|string toValue, Object options, function callback)](animation/worklet.spring.html)

基于物理的动画。

### [#](#AnimationObject-worklet-decay-Object-options-function-callback) [AnimationObject worklet.decay(Object options, function callback)](animation/worklet.decay.html)

基于滚动衰减的动画。

### [#](#AnimationObject-worklet-sequence-AnimationObject-animationN) [AnimationObject worklet.sequence(AnimationObject animationN)](combine-animation/worklet.sequence.html)

组合动画序列，依次执行传入的动画。

### [#](#AnimationObject-worklet-repeat-AnimationObject-animation-number-numberOfReps-boolean-reverse-function-callback) [AnimationObject worklet.repeat(AnimationObject animation, number numberOfReps, boolean reverse, function callback)](combine-animation/worklet.repeat.html)

重复执行动画。

### [#](#AnimationObject-worklet-delay-number-delayMS-AnimationObject-delayedAnimation) [AnimationObject worklet.delay(number delayMS, AnimationObject delayedAnimation)](combine-animation/worklet.delay.html)

延迟执行动画。

### [#](#worklet-scrollViewContext-scrollTo-Object-object) [worklet.scrollViewContext.scrollTo(Object object)](base/worklet.scrollViewContext.scrollTo.html)

滚动至指定位置

Incorrect translation.