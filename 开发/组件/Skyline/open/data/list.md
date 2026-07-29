# [#](#open-data-list) open-data-list

> 基础库 3.7.8 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> 相关文档: [聊天工具模式](../framework/open-ability/chatTool.html)、[Skyline 渲染引擎](../framework/runtime/skyline/introduction.html)、[Skyline 迁移起步](../framework/custom-component/glass-easel/migration.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）

## [#](#功能描述) 功能描述

展示微信开放数据。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | type | string |  | 是 | 开放数据类型 |
|  | | 合法值 | 说明 | | --- | --- | | groupMembers | 群成员信息 | | | | | |
|  | members | Array.<string> |  | 否 | 群成员group\_openid列表 |

## [#](#示例代码) 示例代码

```
<open-data-list type="groupMembers" members="{{members}}">
  <view class="userinfo" slot:index>
    <open-data-item class="avatar " type="userAvatar" index="{{index}}" />
    <open-data-item class="" type="userNickName" index="{{index}}" />
  </view>
</open-data-list>
```

Incorrect translation.