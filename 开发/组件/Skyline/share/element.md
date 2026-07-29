# [#](#share-element) share-element

> 基础库 2.16.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

共享元素。

共享元素是一种动画形式，类似于 [flutter Hero](https://flutterchina.club/animations/hero-animations/)动画，表现为元素像是在页面间穿越一样。该组件需与 [page-container](page-container.html) 组件结合使用。

使用时需在当前页放置 `share-element` 组件，同时在 `page-container` 容器中放置对应的 `share-element` 组件，对应关系通过属性值 `key` 映射。当设置 `page-container` 显示时，`transform` 属性为 `true` 的共享元素会产生动画。当前页面容器退出时，会产生返回动画。

1. 使用 `worklet` 函数需要开启开发者工具 "将 JS 编译成 ES5" 或 "编译 worklet 函数" 选项。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | key | string |  | 是 | 映射标记，页面内唯一 | [2.29.2](../framework/compatibility.html) |
|  | transform | boolean | false | 否 | 是否进行动画 | [2.16.0](../framework/compatibility.html) |
|  | duration | number | 300 | 否 | 动画时长，单位毫秒 | [2.16.0](../framework/compatibility.html) |
|  | easing-function | string | ease-out | 否 | `css`缓动函数 | [2.16.0](../framework/compatibility.html) |

## [#](#Skyline-特有属性) Skyline 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | transition-on-gesture | boolean | false | 否 | 手势返回时是否进行动画 | [2.29.2](../framework/compatibility.html) |
|  | shuttle-on-push | string | to | 否 | 指定 push 阶段的飞跃物 | [2.30.2](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | from | push 阶段采用源页面节点作为飞跃物 | | to | push 阶段采用目标页面节点作为飞跃物 | | from | pop 阶段采用源页面节点作为飞跃物 | | to | pop 阶段采用目标页面节点作为飞跃物 | | | | | | |
|  | shuttle-on-pop | string | to | 否 | 指定 pop 阶段的飞跃物 | [2.30.2](../framework/compatibility.html) |
|  | worklet:onframe | callback |  | 否 | 动画帧回调 | [2.30.2](../framework/compatibility.html) |
|  | rect-tween-type | string | materialRectArc | 否 | 动画插值曲线 | [2.30.2](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | materialRectArc | 矩形对角动画 | | materialRectCenterArc | 径向动画 | | linear |  | | elasticIn |  | | elasticOut |  | | elasticInOut |  | | bounceIn |  | | bounceOut |  | | bounceInOut |  | | cubic-bezier(x1, y1, x2, y2 | ) | | | | | | |

## [#](#WebView-示例代码) WebView 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/NqVP7ImA73ou "在开发者工具中预览效果")

## [#](#Skyline-示例代码) Skyline 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/t584gymu7VMM "在开发者工具中预览效果")

Incorrect translation.