# [#](#sticky-section) sticky-section

> 基础库 2.29.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> 相关文档: [Skyline 渲染引擎](../framework/runtime/skyline/introduction.html)、[Skyline 迁移起步](../framework/custom-component/glass-easel/migration.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）

## [#](#功能描述) 功能描述

吸顶布局容器，仅支持作为 `<scroll-view type="custom">` 模式的直接子节点

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| push-pinned-header | boolean | true | 否 | 吸顶元素重叠时是否继续上推 |  |
| padding | Array | [0, 0, 0, 0] | 否 | 长度为 4 的数组，按 top、right、bottom、left 顺序指定内边距 | [3.0.0](../framework/compatibility.html) |

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/779n3ymK7HMJ "在开发者工具中预览效果")

Incorrect translation.