# [#](#DraggableSheetContext-scrollTo-Object-object) DraggableSheetContext.scrollTo(Object object)

> 基础库 3.2.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：支持

> 相关文档: [draggable-sheet](../../component/draggable-sheet.html)

## [#](#功能描述) 功能描述

滚动到指定位置。`size` 取值 `[0, 1]`，`size = 1` 时表示撑满 `draggable-sheet` 组件。`size` 和 `pixels` 同时传入时，仅 size 生效。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| size | number |  | 否 | 相对目标位置 |
| pixels | number |  | 否 | 绝对目标位置 |
| animated | boolean | true | 否 | 是否启用滚动动画 |
| duration | number | 300 | 否 | 滚动动画时长（ms) |
| easingFunction | string | ease | 否 | 缓动函数 |

## [#](#示例代码) 示例代码

```
Page({
  onReady() {
    this.createSelectorQuery()
      .select(".sheet")
      .node()
      .exec(res => {
        const sheetContext = res[0].node
        sheetContext.scrollTo({
          size: 0.7,
          animated: true,
          duration: 300,
          easingFunction: 'ease'
        })
  },
})
```

Incorrect translation.