# [#](#SelectorQuery) SelectorQuery

> 相关文档: [获取界面上的节点信息](../../framework/view/selector.html)

查询节点信息的对象

## [#](#方法) 方法

### [#](#SelectorQuery-SelectorQuery-in-Component-component) [SelectorQuery SelectorQuery.in(Component component)](SelectorQuery.in.html)

将选择器的选取范围更改为自定义组件 `component` 内。（初始时，选择器仅选取页面范围的节点，不会选取任何自定义组件中的节点）。

### [#](#NodesRef-SelectorQuery-select-string-selector) [NodesRef SelectorQuery.select(string selector)](SelectorQuery.select.html)

在当前页面下选择第一个匹配选择器 `selector` 的节点。返回一个 `NodesRef` 对象实例，可以用于获取节点信息。

### [#](#NodesRef-SelectorQuery-selectAll-string-selector) [NodesRef SelectorQuery.selectAll(string selector)](SelectorQuery.selectAll.html)

在当前页面下选择匹配选择器 selector 的所有节点。

### [#](#NodesRef-SelectorQuery-selectViewport) [NodesRef SelectorQuery.selectViewport()](SelectorQuery.selectViewport.html)

选择显示区域。可用于获取显示区域的尺寸、滚动位置等信息。

### [#](#NodesRef-SelectorQuery-exec-function-callback) [NodesRef SelectorQuery.exec(function callback)](SelectorQuery.exec.html)

执行所有的请求。请求结果按请求次序构成数组，在callback的第一个参数中返回。

Incorrect translation.