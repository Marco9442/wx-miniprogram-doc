# [#](#grid-builder) grid-builder

> 基础库 3.4.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> 相关文档: [Skyline 渲染引擎](../framework/runtime/skyline/introduction.html)、[Skyline 迁移起步](../framework/custom-component/glass-easel/migration.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）

## [#](#功能描述) 功能描述

网格构造器，仅支持作为 `<scroll-view type="custom">` 模式的直接子节点。具体用法可参考 [scroll-view](scroll-view.html#列表构造器使用方法)

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | padding | Array | [0, 0, 0, 0] | 否 | 长度为 4 的数组，按 top、right、bottom、left 顺序指定内边距 |
|  | list | Array |  | 是 | 需要用于渲染的列表 |
|  | child-count | Array |  | 否 | 完整列表的长度，如果不传则取 list 的长度作为其值 |
|  | type | string | aligned | 是 | 布局方式 |
|  | | 合法值 | 说明 | | --- | --- | | aligned | 每行高度由同一行中最大高度子节点决定 | | masonry | 瀑布流，根据子元素高度自动布局 | | | | | |
|  | cross-axis-count | number | 2 | 否 | 交叉轴元素数量 |
|  | max-cross-axis-extent | number | 0 | 否 | 交叉轴元素最大范围 |
|  | main-axis-gap | number | 0 | 否 | 主轴方向间隔 |
|  | cross-axis-gap | number | 0 | 否 | 交叉轴方向间隔 |
|  | binditembuild | eventhandle |  | 否 | 列表项创建时触发，event.detail = {index}，index 即被创建的列表项序号 |
|  | binditemdispose | eventhandle |  | 否 | 列表项回收时触发，event.detail = {index}，index 即被回收的列表项序号 |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: 目前只支持纵向滚动列表
2. `bug`: 目前 `grid-builder` 在进入屏幕后不允许再被滚动出屏幕，否则会被判定成列表需要重新布局进而自动滚动到 `grid-builder` 的顶端

## [#](#使用方法) 使用方法

```
<scroll-view
  type="custom"
  scroll-y
>
   <grid-builder
    list="{{list}}"
    child-count="{{list.length}}"
    cross-axis-count="4"
    cross-axis-gap="8"
    main-axis-gap="8"
  >
    <view slot:item slot:index style="height: 200px;">
      <view>{{item.id}}-{{index}}</view>
    </view>
  </grid-builder>
</scroll-view>
```

Incorrect translation.