# [#](#AnimationObject-worklet-timing-number-toValue-Object-options-function-callback) AnimationObject worklet.timing(number toValue, Object options, function callback)

> **小程序插件**：不支持

> 相关文档: [worklet 动画](../../../../framework/runtime/skyline/worklet.html)

## [#](#功能描述) 功能描述

基于时间的动画。

## [#](#参数) 参数

### [#](#number-toValue) number toValue

目标值

### [#](#Object-options) Object options

动画配置

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| duration | number | 300 | 否 | 动画时长 |
| easing | function | Easing.inOut(Easing.quad) | 否 | 动画曲线，参考 [Easing](worklet.Easing.html) 模块。 |

### [#](#function-callback) function callback

动画完成回调。动画被取消时，返回 fasle，正常完成时返回 true。

## [#](#返回值) 返回值

### [#](#AnimationObject) AnimationObject

返回 `AnimationObject` 类型值，可直接赋值给 `SharedValue`。

## [#](#示例代码) 示例代码

```
<view id="moved-box"></view>
<view id="btn" bind:tap="tap">点击驱动小球移动</view>
</code>

<code>
const { shared, timing, Easing } = wx.worklet
Page({
  onLoad() {
    const offset = shared(0)
    this.applyAnimatedStyle('#moved-box', () => {
      'worklet';
      return {
        transform: `translateX(${offset.value}px)`
      }
    })
    this._offset = offset
  }
  tap() {
    const random = Math.random()
    this._offset.value = timing(random, {
        duration: 500,
        easing: Easing.bezier(0.25, 0.1, 0.25, 1),
      }),
    };
})
```

Incorrect translation.