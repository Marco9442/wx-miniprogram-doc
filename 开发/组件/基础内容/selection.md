# [#](#selection) selection

> 基础库 3.6.4 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

渲染框架支持情况：WebView

## [#](#功能描述) 功能描述

局部文本选区。

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| disable-context-menu | boolean | false | 否 | 是否隐藏客户端原生文本选区按钮 | [3.6.4](../framework/compatibility.html) |
| bindselectionchange | eventhandle |  | 否 | 当选区发生变化时触发 selectionchange 事件 event.detail = { isCollapsed, selectedString, firstNodeId, firstOffset, lastNodeId, lastOffset, firstRangeRect } | [3.6.4](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: 长按选区在 `wx-selection` 内才可以触发 disable-context-menu 的效果
2. `tip`: `text` 和 `rich-text` 组件需要设置 `user-select` 为 `true`。
3. `tip`: `firstNodeId` 和 `lastNodeId` 需要 `text` 和 `rich-text` 组件设置 `id`。
4. `tip`: 超出 `wx-selection` 的情况下 `firstOffset` 和 `lastOffset` 为空。

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/nwLKK6mU7VVb "在开发者工具中预览效果")

Incorrect translation.