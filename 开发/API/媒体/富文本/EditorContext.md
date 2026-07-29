# [#](#EditorContext) EditorContext

> 基础库 2.7.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> 相关文档: [editor 组件](../../../component/editor.html)

EditorContext 实例，可通过 [wx.createSelectorQuery](../../wxml/wx.createSelectorQuery.html) 获取。

[EditorContext](EditorContext.html) 通过 `id` 跟一个 [editor](../../../component/editor.html) 组件绑定，操作对应的 [editor](../../../component/editor.html) 组件。

## [#](#方法) 方法

### [#](#EditorContext-format-string-name-string-value) [EditorContext.format(string name, string value)](EditorContext.format.html)

修改样式

### [#](#EditorContext-insertDivider) [EditorContext.insertDivider()](EditorContext.insertDivider.html)

插入分割线

### [#](#EditorContext-insertImage-Object-object) [EditorContext.insertImage(Object object)](EditorContext.insertImage.html)

插入图片。

地址为临时文件时，获取的编辑器html格式内容中 ![]() 标签增加属性 data-local，delta 格式内容中图片 attributes 属性增加 data-local 字段，该值为传入的临时文件地址。

开发者可选择在提交阶段上传图片到服务器，获取到网络地址后进行替换。替换时对于html内容应替换掉 ![]() 的 src 值，对于 delta 内容应替换掉 `insert { image: abc }` 值。

### [#](#EditorContext-insertText-Object-object) [EditorContext.insertText(Object object)](EditorContext.insertText.html)

覆盖当前选区，设置一段文本

### [#](#EditorContext-setContents-Object-object) [EditorContext.setContents(Object object)](EditorContext.setContents.html)

初始化编辑器内容，html和delta同时存在时仅delta生效

### [#](#EditorContext-getContents) [EditorContext.getContents()](EditorContext.getContents.html)

获取编辑器内容

### [#](#EditorContext-clear) [EditorContext.clear()](EditorContext.clear.html)

清空编辑器内容

### [#](#EditorContext-removeFormat) [EditorContext.removeFormat()](EditorContext.removeFormat.html)

清除当前选区的样式

### [#](#EditorContext-undo) [EditorContext.undo()](EditorContext.undo.html)

撤销

### [#](#EditorContext-redo) [EditorContext.redo()](EditorContext.redo.html)

恢复

### [#](#EditorContext-getHistoryState) [EditorContext.getHistoryState()](EditorContext.getHistoryState.html)

获取历史操作状态

### [#](#EditorContext-blur) [EditorContext.blur()](EditorContext.blur.html)

编辑器失焦，同时收起键盘。

### [#](#EditorContext-scrollIntoView) [EditorContext.scrollIntoView()](EditorContext.scrollIntoView.html)

使得编辑器光标处滚动到窗口可视区域内。

### [#](#EditorContext-getSelectionText) [EditorContext.getSelectionText()](EditorContext.getSelectionText.html)

获取编辑器已选区域内的纯文本内容。当编辑器失焦或未选中一段区间时，返回内容为空。

### [#](#EditorContext-insertCustomBlock-Object-object) [EditorContext.insertCustomBlock(Object object)](EditorContext.insertCustomBlock.html)

插入自定义区块

### [#](#EditorContext-getSelection) [EditorContext.getSelection()](EditorContext.getSelection.html)

获取当前选区

### [#](#EditorContext-setSelection-Object-object) [EditorContext.setSelection(Object object)](EditorContext.setSelection.html)

设置当前选区

### [#](#EditorContext-getBounds-Object-object) [EditorContext.getBounds(Object object)](EditorContext.getBounds.html)

获取指定选区的位置和大小

### [#](#EditorContext-deleteText-Object-object) [EditorContext.deleteText(Object object)](EditorContext.deleteText.html)

删除指定选取区的内容

Incorrect translation.