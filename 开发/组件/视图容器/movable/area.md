# [#](#movable-area) movable-area

> 基础库 1.2.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：WebView

## [#](#功能描述) 功能描述

[movable-view](movable-view.html)的可移动区域。

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| scale-area | Boolean | false | 否 | 当里面的movable-view设置为支持双指缩放时，设置此值可将缩放手势生效区域修改为整个movable-area | [1.9.90](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: movable-area 必须设置width和height属性，不设置默认为10px\*\*
2. `tip`: 当movable-view小于movable-area时，movable-view的移动范围是在movable-area内；
3. `tip`: 当movable-view大于movable-area时，movable-view的移动范围必须包含movable-area（x轴方向和y轴方向分开考虑）
4. `tip`: 若当前组件所在的页面或全局开启了 `enablePassiveEvent` 配置项，该内置组件可能会出现非预期表现（详情参考 [enablePassiveEvent 文档](../reference/configuration/app)）

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/1g3lR6mv73lm "在开发者工具中预览效果")

Incorrect translation.