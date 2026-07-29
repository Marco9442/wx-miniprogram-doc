# [#](#list-builder) list-builder

> 基础库 3.3.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> 相关文档: [Skyline 渲染引擎](../framework/runtime/skyline/introduction.html)、[Skyline 迁移起步](../framework/custom-component/glass-easel/migration.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）

## [#](#功能描述) 功能描述

列表构造器，仅支持作为 `<scroll-view type="custom">` 模式的直接子节点。具体用法可参考 [scroll-view](scroll-view.html#列表构造器使用方法)

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | padding | Array | [0, 0, 0, 0] | 否 | 长度为 4 的数组，按 top、right、bottom、left 顺序指定内边距 |  |
|  | type | string | static | 是 | 类型，默认为定高模式 |  |
|  | | 合法值 | 说明 | | --- | --- | | static | 定高模式，所有列表项等高，需要传入 child-height | | dynamic | 不定高模式 | | | | | | |
|  | list | Array |  | 是 | 需要用于渲染的列表 |  |
|  | child-count | Array |  | 否 | 完整列表的长度，如果不传则取 list 的长度作为其值 |  |
|  | child-height | Array |  | 否 | 列表项的高度，当 type 为 static 时必须传入 |  |
|  | binditembuild | eventhandle |  | 否 | 列表项创建时触发，event.detail = {index}，index 即被创建的列表项序号 |  |
|  | binditemdispose | eventhandle |  | 否 | 列表项回收时触发，event.detail = {index}，index 即被回收的列表项序号 |  |
|  | initial-child-count | number | 0 | 否 | 首次渲染时渲染的列表项数量，用于减少首次渲染时的白屏时长。不传则首屏也根据布局结果按需渲染 | [3.7.12](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: 目前只支持纵向滚动列表

## [#](#使用方法) 使用方法

```
<scroll-view
  type="custom"
  scroll-y
>
   <list-builder
    list="{{list}}"
    child-count="{{list.length}}"
    child-height="200"
  >
    <view slot:item slot:index style="height: 200px;">
      <view>{{item.id}}-{{index}}</view>
    </view>
  </list-builder>
</scroll-view>
```

Incorrect translation.