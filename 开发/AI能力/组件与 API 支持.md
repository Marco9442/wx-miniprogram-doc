# [#](#组件支持列表) 组件支持列表

原子组件可使用的内置组件有限，目前支持的组件如下表：

| 组件 | 支持范围 |
| --- | --- |
| view | 支持 |
| text | 不支持 user-select |
| map | 不支持拖动、放大交互，MapContext 的支持见「[API 支持列表](api)」，通过 [this.createSelectorQuery](https://developers.weixin.qq.com/miniprogram/dev/api/wxml/SelectorQuery.html) 获取 MapContext |
| button | 不支持所有 open-type |
| image | 仅支持网络地址，仅支持 png、jpg 格式 |
| canvas | 仅支持 2d，通过 [this.createSelectorQuery](https://developers.weixin.qq.com/miniprogram/dev/api/wxml/SelectorQuery.html) 获取 Context |
| scroll-view | 仅支持横向滚动（scroll-x） |
| collapsible-view | 支持 |

Incorrect translation.