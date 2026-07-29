# [#](#official-account-publish) official-account-publish

> 基础库 3.9.3 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

渲染框架支持情况：WebView

## [#](#功能描述) 功能描述

贴图组件。

贴图组件为小程序开发者提供了在小程序里直接发表和消费贴图的能力。
该组件可以帮助开发者实现社区讨论、用户交流的功能，并且让更多人通过贴图发现小程序。

## [#](#话题定制) 话题定制

贴图组件上会展示话题名称，用户从组件发表时也会默认带上对应的#话题。默认使用小程序名称作为话题，开发者也可通过`topic`参数自定义，最多20字。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/fef8bdbf-7f32-49b7-8437-c3a56b62cb6d.png)

## [#](#内容展示) 内容展示

- 组件里会展示从该组件发表的所有贴图（如果一个小程序里有多个同话题名称的组件，其下的贴图也会互通展示）。
- 通过`limit`参数控制最多展示的贴图数量，上限10条。
- 当组件下内容为空时，默认显示“来写下第一条吧”，可通过`placeholder`参数自定义文案，最多显示一行。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/9b454a52-1063-480c-a432-78b48cb71bac.png)

## [#](#相关内容) 相关内容

修改话题名称后，历史发表内容不会在新话题中展示。为保留历史内容沉淀，在话题组件下方的“相关内容”区域可展示不在此话题下的历史发表内容。该区域默认展示，可通过`show-related`参数设置不展示。

![](https://res.wx.qq.com/op_res/37H9vU7VKzcOTNT0zdLVW_Ep5GQhHPA83JPSn1zbtzxD-MmXgMs3DFHWR09H4Yihag1RexqNJMqufs5F9eXK2A)

## [#](#推荐用户添加指定链接) 推荐用户添加指定链接

设置`recommend-path`和`recommend-title`参数，编辑器支持推荐自定义标题的小程序链接，用户点击添加后将在正文展示链接卡片。

![](https://res.wx.qq.com/op_res/ZipPIHAvNuPZxOY1SU2YlAGagDst5goTLdFYrPPIXjLhBDLn7A6AWu-Wcft498gHPcPmPFy2l6122ZTvJNKteg)

![](https://res.wx.qq.com/op_res/ZipPIHAvNuPZxOY1SU2YlOmyPnsWUXdQPbrvUKLkos-qWG_nNtsDwXB7G8XTDeKOhNlQpEFtYab28n3OCEYoWw)

## [#](#内容管理) 内容管理

- 可以前往小程序后台对单条贴图进行置顶或拉黑（路径：开发管理 → 接口设置 → 接口权限 → 其它组件 → 贴图）。
- 同一个话题下最多置顶3条贴图。
- 小程序后台支持查看每个组件下的基础数据。

![](https://res.wx.qq.com/op_res/BAS89qUEncrqPBvvs43Q3s-HOnkE6cNQvr67WQgoOR_No_YDEaJJXHYyRnZXhGvLs1yg9szspCOxOuzQNvSxCA)

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| topic | string |  | 否 | 话题名称，最多20字，默认使用小程序名称 | [3.9.3](../framework/compatibility.html) |
| limit | number | 4 | 否 | 小程序页面内最多展示的贴图数量，超出后剩余的贴图需要点击「查看更多」前往查看 | [3.10.3](../framework/compatibility.html) |
| background-color | color | #f7f7f7 | 否 | 贴图组件的背景颜色 | [3.9.3](../framework/compatibility.html) |
| color-unity | boolean | false | 否 | 是否需要色彩统一，话题名称颜色和贴图卡片背景颜色是否对齐 | [3.9.3](../framework/compatibility.html) |
| placeholder | string | 来写下第一条吧 | 否 | 无内容时的占位文案 | [3.10.2](../framework/compatibility.html) |
| show-related | boolean | true | 否 | 是否展示相关内容 | [3.16.0](../framework/compatibility.html) |
| recommend-path | string |  | 否 | 贴图链接卡片跳转页面 | [3.16.1](../framework/compatibility.html) |
| recommend-title | string |  | 否 | 贴图链接卡片标题 | [3.16.1](../framework/compatibility.html) |
| binderror | eventhandle |  | 否 | 列表拉取失败时触发 | [3.9.3](../framework/compatibility.html) |
| bindempty | eventhandle |  | 否 | 列表拉取为空时触发 | [3.9.3](../framework/compatibility.html) |
| bindpublishsuccess | eventhandle |  | 否 | 发表成功时触发，在e.detail中可获取发表的贴图链接postUrl（只有在真正发表完成后链接才可访问） | [3.11.3](../framework/compatibility.html) |
| bindpublishfail | eventhandle |  | 否 | 发表失败时触发 | [3.11.3](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`：暂不支持在微信 Windows 版、微信 Mac 版及微信鸿蒙版本的小程序上显示发表按钮。
2. `tip`：话题名称要求不超过20字，超过将不展示该组件。

## [#](#示例代码) 示例代码

```
<official-account-publish topic="和coco一起做好事"></official-account-publish>
```

Incorrect translation.