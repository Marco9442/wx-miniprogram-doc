# [#](#wx-joinVoIPChat-Object-object) wx.joinVoIPChat(Object object)

> 基础库 2.7.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **[用户授权](../../../framework/open-ability/authorize.html)**：需要 scope.record
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.9.0](../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [多人音视频对话](../../../framework/open-ability/voip-chat.html)

## [#](#功能描述) 功能描述

加入 (创建) 实时语音通话，更多信息可见 [实时语音指南](../../../framework/open-ability/voip-chat.html)。调用前需要用户授权 `scope.record`，若房间类型为视频房间需要用户授权 `scope.camera`。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | roomType | String | voice | 否 | 房间类型 |  |
|  | | 合法值 | 说明 | | --- | --- | | voice | 音频房间，用于语音通话 | | video | 视频房间，结合 [voip-room](../../../component/voip-room.html) 组件可显示成员画面 | | | | | | |
|  | signature | String |  | 是 | 签名，用于验证小游戏的身份 |  |
|  | nonceStr | String |  | 是 | 验证所需的随机字符串 |  |
|  | timeStamp | Number |  | 是 | 验证所需的时间戳 |  |
|  | groupId | String |  | 是 | 小游戏内此房间/群聊的 ID。同一时刻传入相同 groupId 的用户会进入到同个实时语音房间。 |  |
|  | muteConfig | Object |  | 否 | 静音设置 |  |
|  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | muteMicrophone | Boolean | false | 否 | 是否静音麦克风 | |  | muteEarphone | Boolean | false | 否 | 是否静音耳机 | | | | | | |
|  | forceCellularNetwork | boolean | false | 否 | 开启后，joinVoIPChat 会同时走 Wi-Fi 和蜂窝网络2种网络模式，保证实时通话体验。 | [2.29.0](../../../framework/compatibility.html) |
|  | success | function |  | 否 | 接口调用成功的回调函数 |  |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |  |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| openIdList | Array.<String> | 在此通话中的成员 openId 名单 |
| errCode | Number | 错误码 |
| errMsg | String | 调用结果 |

## [#](#错误) 错误

| 错误码 | 错误信息 | 说明 |
| --- | --- | --- |
| -1 | 当前已在房间内 |  |
| -2 | 录音设备被占用，可能是当前正在使用微信内语音通话或系统通话 |  |
| -3 | 加入会话期间退出（可能是用户主动退出，或者退后台、来电等原因），因此加入失败 |  |
| -1000 | 系统错误 |  |

Incorrect translation.