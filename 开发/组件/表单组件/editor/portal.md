# [#](#editor-portal) editor-portal

> 基础库 3.7.11 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：WebView

## [#](#功能描述) 功能描述

渲染 [editor](editor.html) 组件的自定义区块。相关接口 [EditorCtx.insertCustomBlock](../api/media/editor/EditorContext.insertCustomBlock.html)。

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| key | string |  | 是 | 自定义区块的 blockId |

## [#](#使用方法) 使用方法

### [#](#插入自定义区块) 插入自定义区块

1. 使用 `EditorContext.insertCustomBlock` 插入自定义区块（此时仅占位），获取返回的 `blockId`；
2. 渲染 `<editor-portal>` 组件，并指定 `key` 属性为 `blockId`，`<editor-portal>` 中的内容将插入到自定义区块的位置;

### [#](#重新渲染自定义区块) 重新渲染自定义区块

自定义区块的结构和数据需要分开存储。建议编辑区内容使用返回的`delta` 数据结构存储，更为精简。

1. 通过 `EditorContext.getContents` 获取编辑区内容，此时 `delta` 中自定义块仅保存对应的 `blockId`;
2. 开发者需自行保存自定义块对应的数据内容，按 `blockId` 映射；
3. 通过 `EditorContext.setContents` 设置编辑区内容时，同时渲染 `<editor-portal>` 组件替换自定义区块的内容；

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/p1CNqCmY7vY0 "在开发者工具中预览效果")

```
<editor id="editor">
  <block wx:for="{{customBlockList}}" wx:key="blockId">
    <editor-portal key="{{item.blockId}}">
      <view class="flex"></view>
    </editor-portal>
  </block>
</editor>
```

```
Page({
  insertCustomBlock() {
    const { customBlockList } = this.data
    this.editorCtx.insertCustomBlock({
      success:(res) => {
        customBlockList.push({
          blockId: res.blockId
        })
        this.setData({ customBlockList })
      }
    })
  }
})
```

Incorrect translation.