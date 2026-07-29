# [#](#SelectorQuery-NodesRef-ref-function-callback) [SelectorQuery](SelectorQuery.html) NodesRef.ref(function callback)

> 基础库 3.3.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：支持

> 相关文档: [获取界面上的节点信息](../../framework/view/selector.html) [scrollViewContext](../ui/worklet/base/worklet.scrollViewContext.scrollTo.html)

## [#](#功能描述) 功能描述

获取 `Node` 节点的 Ref 对象，可用于 `worklet` 函数内操作节点。仅 `Skyline` 下支持，`Node` 必须是非 `virtual` 类型。

## [#](#参数) 参数

### [#](#function-callback) function callback

回调函数，在执行 `SelectorQuery.exec` 方法后，返回节点 Ref 对象。

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| ref | Object | 节点对应的 Ref 对象 |

## [#](#返回值) 返回值

### [#](#SelectorQuery) [SelectorQuery](SelectorQuery.html)

## [#](#示例代码) 示例代码

```
Page({
  getNode() {
    this.createSelectorQuery().select('.scrollable').ref(function(res){
      console.log(res.ref) // 节点对应的 Ref 对象
    }).exec()
  }
})
```

Incorrect translation.