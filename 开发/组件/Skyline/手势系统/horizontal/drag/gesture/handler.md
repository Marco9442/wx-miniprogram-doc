# [#](#horizontal-drag-gesture-handler) horizontal-drag-gesture-handler

> 相关文档: [手势系统](../framework/runtime/skyline/gesture.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）

## [#](#功能描述) 功能描述

横向滑动时触发手势

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | tag | string |  | 否 | 声明手势协商时的组件标识 |
|  | worklet:ongesture | eventhandler |  | 否 | 手势识别成功的回调 |
|  | | eventhandler 回调参数 | 说明 | | --- | --- | | state | 手势状态 | | absoluteX | 相对于全局的 X 坐标 | | absoluteY | 相对于全局的 Y 坐标 | | deltaX | 相对上一次，X 轴方向移动的坐标 | | deltaY | 相对上一次，Y 轴方向移动的坐标 | | velocityX | 手指离开屏幕时的横向速度（pixel per second) | | velocityY | 手指离开屏幕时的纵向速度（pixel per second) | | | | | |
|  | worklet:should-response-on-move | callback |  | 否 | 手指移动过程中手势是否响应 |
|  | worklet:should-accept-gesture | callback |  | 否 | 手势是否应该被识别 |
|  | simultaneous-handlers | Array.<string> |  | 否 | 声明可同时触发的手势节点 |
|  | native-view | string |  | 否 | 代理的原生节点类型 |

Incorrect translation.