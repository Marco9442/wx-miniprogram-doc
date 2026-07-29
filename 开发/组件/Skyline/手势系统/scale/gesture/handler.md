# [#](#scale-gesture-handler) scale-gesture-handler

> 相关文档: [手势系统](../framework/runtime/skyline/gesture.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）

## [#](#功能描述) 功能描述

多指缩放时触发手势

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | tag | string |  | 否 | 声明手势协商时的组件标识 |
|  | worklet:ongesture | eventhandler |  | 否 | 手势识别成功的回调 |
|  | | eventhandler 回调参数 | 说明 | | --- | --- | | state | 手势状态 | | focalX | 中心点相对于全局的X坐标 | | focalY | 中心点相对于全局的Y坐标 | | focalDeltaX | 相对上一次，中心点在X轴方向移动的坐标 | | focalDeltaY | 相对上一次，中心点在Y轴方向移动的坐标 | | scale | 放大或缩小的比例 | | horizontalScale | scale的横向分量 | | verticalScale | scale的纵向分量 | | rotation | 旋转角（单位：弧度） | | velocityX | 手指离开屏幕时的横向速度（pixel per second) | | velocityY | 手指离开屏幕时的纵向速度（pixel per second) | | pointerCount | 跟踪的手指数 | | | | | |
|  | worklet:should-response-on-move | callback |  | 否 | 手指移动过程中手势是否响应 |
|  | worklet:should-accept-gesture | callback |  | 否 | 手势是否应该被识别 |
|  | simultaneous-handlers | Array.<string> |  | 否 | 声明可同时触发的手势节点 |
|  | native-view | string |  | 否 | 代理的原生节点类型 |

Incorrect translation.