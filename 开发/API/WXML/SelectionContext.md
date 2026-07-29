# [#](#SelectionContext) SelectionContext

> 基础库 3.16.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> 相关文档: [selection](../../component/selection.html)

SelectionContext 实例，可通过 [SelectorQuery.context](NodesRef.context.html) 获取。

[SelectionContext](SelectionContext.html) 通过 `id` 跟一个 [selection](../../component/selection.html) 组件绑定，可主动控制组件内部选区。

## [#](#方法) 方法

### [#](#SelectionContext-selectRange-number-start-number-end) [SelectionContext.selectRange(number start, number end)](SelectionContext.selectRange.html)

主动设置 [selection](../../component/selection.html) 组件内部选区范围。偏移以组件内所有有效 [text](../../component/text.html) 单元拼接后的字符串为准。

### [#](#SelectionContext-removeSelection) [SelectionContext.removeSelection()](SelectionContext.removeSelection.html)

清除 [selection](../../component/selection.html) 组件内部当前选区。

## [#](#示例代码) 示例代码

```
<selection id="selection">
  <text user-select>abcdefg</text>
</selection>
```

```
Page({
  onReady() {
    wx.createSelectorQuery().select('#selection').context(ctx => {
      this.selectionContext = ctx
    }).exec()
  },
  selectPart() {
    this.selectionContext.selectRange(1, 5)
  },
  clearSelection() {
    this.selectionContext.removeSelection()
  },
})
```

Incorrect translation.