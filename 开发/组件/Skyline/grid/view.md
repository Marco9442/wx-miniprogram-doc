# [#](#grid-view) grid-view

> 基础库 2.29.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> 相关文档: [Skyline 渲染引擎](../framework/runtime/skyline/introduction.html)、[Skyline 迁移起步](../framework/custom-component/glass-easel/migration.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）

## [#](#功能描述) 功能描述

Skyline 下网格布局容器 和 瀑布流布局容器。基础库版本 2.30.4 起提供 WebView 兼容实现。

1. 仅支持作为 `<scroll-view type="custom">` 模式的直接子节点
2. 按需渲染节点，比 WebView 兼容实现具备更好的性能。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | type | string | aligned | 是 | 布局方式 |  |
|  | | 合法值 | 说明 | | --- | --- | | aligned | 每行高度由同一行中最大高度子节点决定 | | masonry | 瀑布流，根据子元素高度自动布局 | | | | | | |
|  | cross-axis-count | number | 2 | 否 | 交叉轴元素数量 |  |
|  | max-cross-axis-extent | number | 0 | 否 | 交叉轴元素最大范围 |  |
|  | main-axis-gap | number | 0 | 否 | 主轴方向间隔 |  |
|  | cross-axis-gap | number | 0 | 否 | 交叉轴方向间隔 |  |
|  | padding | Array | [0, 0, 0, 0] | 否 | 长度为 4 的数组，按 top、right、bottom、left 顺序指定内边距 | [3.0.0](../framework/compatibility.html) |

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/hc924ymg7OMi "在开发者工具中预览效果")

## [#](#Tip) Tip

在 WebView 下且 `type="masonry"` 时，grid-view 的子元素：

1. 需具有可见的宽高（`clientWidth` 和 `clientHeight`）。例如：
   设置 `display: block` 属性；
   使用 image 组件时，应当手动指定高度或设置 `mode="widthFix"`。
2. 若使用 `padding`、`margin` 等影响盒模型的CSS属性，需同时设置 `box-sizing: border`。
3. 仅针对在末尾增删元素做优化，尽量避免在中间插入子元素。
4. 子节点过多时仍会影响布局性能。对性能敏感的场景，建议使用 Skyline 对应组件。

Incorrect translation.