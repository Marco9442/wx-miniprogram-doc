# [#](#DraggableSheetContext) DraggableSheetContext

> 基础库 3.2.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> 相关文档: [draggable-sheet](../../component/draggable-sheet.html)

DraggableSheet 实例，可通过 [wx.createSelectorQuery](../wxml/wx.createSelectorQuery.html) 的 [NodesRef.node](../wxml/NodesRef.node.html) 方法获取。

## [#](#方法) 方法

### [#](#DraggableSheetContext-scrollTo-Object-object) [DraggableSheetContext.scrollTo(Object object)](DraggableSheetContext.scrollTo.html)

滚动到指定位置。`size` 取值 `[0, 1]`，`size = 1` 时表示撑满 `draggable-sheet` 组件。`size` 和 `pixels` 同时传入时，仅 size 生效。

Incorrect translation.