# [#](#picker-view-column) picker-view-column

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

滚动选择器子项。仅可放置于[picker-view](picker-view.html)中，其孩子节点的高度会自动设置成与[picker-view](picker-view.html)的选中框的高度一致

## [#](#Bug-Tip) Bug & Tip

1. `tip`: 若当前组件所在的页面或全局开启了 `enablePassiveEvent` 配置项，该内置组件可能会出现非预期表现（详情参考 [enablePassiveEvent 文档](../reference/configuration/app)）
2. `tip`: 子节点建议添加 `aria-role=option` 和 `aria-label` 以增强无障碍支持。

Incorrect translation.