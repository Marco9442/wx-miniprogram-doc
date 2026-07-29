# [#](#AnimationObject-worklet-spring-number-string-toValue-Object-options-function-callback) AnimationObject worklet.spring(number|string toValue, Object options, function callback)

> **小程序插件**：不支持

> 相关文档: [worklet 动画](../../../../framework/runtime/skyline/worklet.html)

## [#](#功能描述) 功能描述

基于物理的动画。

## [#](#参数) 参数

### [#](#number-string-toValue) number|string toValue

目标值

### [#](#Object-options) Object options

动画配置

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| damping | number | 10 | 否 | 阻尼系数 |
| mass | number | 1 | 否 | 重量系数，值越大移动越慢 |
| stiffness | number | 100 | 否 | 弹性系数 |
| overshootClamping | boolean | false | 否 | 动画是否可以在指定值上反弹 |
| restDisplacementThreshold | number | 0.01 | 否 | 弹簧静止时的位移 |
| restSpeedThreshold | number | 2 | 否 | 弹簧静止的速度 |
| velocity | number | 0 | 否 | 速度 |

### [#](#function-callback) function callback

动画完成回调。动画被取消时，返回 fasle，正常完成时返回 true。

## [#](#返回值) 返回值

### [#](#AnimationObject) AnimationObject

返回 `AnimationObject` 类型值，可直接赋值给 `SharedValue`。

## [#](#示例代码) 示例代码

```
<pan-gesture-handler onGestureEvent="handlepan">
  <view class="circle"></view>
</pan-gesture-handler>
</code>

<code>
const { shared, spring } = wx.worklet
Page({
  onLoad() {
    const offset = shared(0);
    this.applyAnimatedStyle(".circle", () => {
      "worklet";
      return {
        transform: `translateX${offset.value}px`,
      };
    });
    this._offset = offset;
  },
  handlepan(evt) {
    "worklet";
    if (evt.state === GestureState.ACTIVE) {
      this._offset.value += evt.deltaX;
    } else if (evt.state === GestureState.END) {
      this._offset.value = spring(0);
    }
  },
});
```

Incorrect translation.