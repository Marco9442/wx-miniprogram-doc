# [#](#NodesRef-SelectorQuery-selectAll-string-selector) [NodesRef](NodesRef.html) SelectorQuery.selectAll(string selector)

> **小程序插件**：支持

> 相关文档: [获取界面上的节点信息](../../framework/view/selector.html)

## [#](#功能描述) 功能描述

在当前页面下选择匹配选择器 selector 的所有节点。

## [#](#参数) 参数

### [#](#string-selector) string selector

选择器

## [#](#返回值) 返回值

### [#](#NodesRef) [NodesRef](NodesRef.html)

## [#](#selector-语法) selector 语法

selector类似于 CSS 的选择器，但仅支持下列语法。

- ID选择器：#the-id
- class选择器（可以连续指定多个）：.a-class.another-class
- 子元素选择器：.the-parent > .the-child
- 后代选择器：.the-ancestor .the-descendant
- 跨自定义组件的后代选择器：.the-ancestor >>> .the-descendant
- 多选择器的并集：#a-node, .some-other-nodes

Incorrect translation.