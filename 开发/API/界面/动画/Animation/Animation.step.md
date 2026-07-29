# [#](#Animation-Animation-step-Object-object) [Animation](Animation.html) Animation.step(Object object)

> **小程序插件**：支持

> 相关文档: [动画](../../../framework/view/animation.html)

## [#](#功能描述) 功能描述

表示一组动画完成。可以在一组动画中调用任意多个动画方法，一组动画中的所有动画会同时开始，一组动画完成后才会进行下一组动画。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | duration | number | 400 | 否 | 动画持续时间，单位 ms |
|  | timingFunction | string | 'linear' | 否 | 动画的效果 |
|  | | 合法值 | 说明 | | --- | --- | | 'linear' | 动画从头到尾的速度是相同的 | | 'ease' | 动画以低速开始，然后加快，在结束前变慢 | | 'ease-in' | 动画以低速开始 | | 'ease-in-out' | 动画以低速开始和结束 | | 'ease-out' | 动画以低速结束 | | 'step-start' | 动画第一帧就跳至结束状态直到结束 | | 'step-end' | 动画一直保持开始状态，最后一帧跳到结束状态 | | | | | |
|  | delay | number | 0 | 否 | 动画延迟时间，单位 ms |
|  | transformOrigin | string | '50% 50% 0' | 否 |  |

## [#](#返回值) 返回值

### [#](#Animation) [Animation](Animation.html)

animation

Incorrect translation.