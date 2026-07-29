# [#](#voip-room) voip-room

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 鸿蒙 OS 版**：支持

> 相关文档: [wx.joinVoIPChat](../api/media/voip/wx.joinVoIPChat.html)

渲染框架支持情况：WebView

## [#](#功能描述) 功能描述

多人音视频对话。需[用户授权](../framework/open-ability/authorize.html) `scope.camera`、`scope.record`。

## [#](#申请开通) 申请开通

暂只针对国内主体如下类目的小程序开放，需要先通过类目审核，再在小程序管理后台，「开发」-「接口设置」中自助开通该组件权限。

| 一级类目/主体类型 | 二级类目 | 小程序内容场景 |
| --- | --- | --- |
| 教育 | 在线视频课程 | 网课、在线培训、讲座等教育类直播 |
| 医疗 | 互联网医院，公立医院 | 问诊、大型健康讲座等直播 |
| 医疗 | 私立医疗机构 | / |
| 金融 | 银行、信托、基金、证券/期货、证券、期货投资咨询、保险、征信业务、新三板信息服务平台、股票信息服务平台（港股/美股）、消费金融 | 金融产品视频客服理赔、金融产品推广直播等 |
| 汽车 | 汽车预售服务 | 汽车预售、推广直播 |
| 政府主体账号 | / | 政府相关工作推广直播、领导讲话直播等 |
| IT 科技 | 多方通信 | 在线会议 |
| 快递业与邮政 | 寄件/收件 | 视频客服 |

开通该组件权限后，开发者可在 `joinVoIPChat` 成功后，获取房间成员的 `openid`，传递给 `voip-room` 组件，以显示成员画面。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | openid | string |  | 是 | 进入房间用户的 openid | [2.11.0](../framework/compatibility.html) |
|  | mode | string | camera | 是 | 对话窗口类型 | [2.11.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | camera | 自身传入 camera | | video | 其他用户传入 video | | | | | | |
|  | device-position | string | front | 是 | 摄像头方向，仅在 mode 为 camera 时有效 | [2.11.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | front | 前置 | | back | 后置 | | | | | | |
|  | object-fit | string | fill | 是 | 画面与容器比例不一致时，画面的表现形式 | [2.29.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | fill | 填充 | | contain | 包含 | | cover | 覆盖，安卓暂未支持，iOS 生效 | | | | | | |
|  | binderror | eventhandle |  | 否 | 创建对话窗口失败时触发 | [2.11.0](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`：开发者工具上暂不支持
2. `tip`：请注意[原生组件使用限制](./native-component.html#原生组件的使用限制)

## [#](#示例代码) 示例代码

```
<block wx:for="{{openIdList}}" wx:key="*this">
  <voip-room
    openid="{{item}}"
    mode="{{selfOpenId === item ? 'camera' : 'video'}}">
  </voip-room>
</block>
```

Incorrect translation.