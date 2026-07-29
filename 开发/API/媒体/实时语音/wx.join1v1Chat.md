# [#](#wx-join1v1Chat-Object-object) wx.join1v1Chat(Object object)

> 基础库 2.20.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **[用户授权](../../../framework/open-ability/authorize.html)**：需要 scope.record,&,camera
>
> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [双人音视频对话](../../../framework/open-ability/1v1voip.html)

## [#](#功能描述) 功能描述

加入（创建）双人通话。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | caller | Object |  | 是 | 呼叫方信息 |
|  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | nickname | String |  | 是 | 昵称 | |  | headImage | String |  | 否 | 头像 | |  | openid | String |  | 是 | 小程序内 openid | | | | | |
|  | listener | Object |  | 是 | 接听方信息 |
|  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | nickname | String |  | 是 | 昵称 | |  | headImage | String |  | 否 | 头像 | |  | openid | String |  | 是 | 小程序内 openid | | | | | |
|  | backgroundType | Number | 0 | 否 | 窗口背景色(音频通话背景以及小窗模式背景) |
|  | | 合法值 | 说明 | | --- | --- | | 0 | #262930 | | 1 | #FA5151 | | 2 | #FA9D3B | | 3 | #3D7257 | | 4 | #1485EE | | 5 | #6467F0 | | | | | |
|  | roomType | String | video | 否 | 通话类型 |
|  | | 合法值 | 说明 | | --- | --- | | voice | 语音通话 | | video | 视频通话 | | | | | |
|  | minWindowType | Number | 1 | 否 | 小窗样式 |
|  | disableSwitchVoice | Boolean | false | 否 | 不允许切换到语音通话 |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#错误) 错误

| 错误码 | 错误信息 | 说明 |
| --- | --- | --- |
| -20000 | not open 1v1 Chat | 未开通双人通话 |
| -20001 | device not support | 当前设备不支持 |
| -20002 | on call | 正在通话中 |
| -20003 | occupied by other miniprogram | 其它小程序正在通话中 |
| -30000 | system error | 内部系统错误 |
| -30001 | wechat has no camera authorization | 微信缺失相机权限 |
| -30002 | wechat has no record authorization | 微信缺失录音权限 |
| -30003 | miniprogram has no record authorization | 小程序缺失录音权限 |
| -30004 | miniprogram has no camera authorization | 小程序缺失相机权限 |
| -1 |  | 当前已在房间内 |
| -2 |  | 录音设备被占用，可能是当前正在使用微信内语音通话或系统通话 |
| -3 |  | 加入会话期间退出（可能是用户主动退出，或者退后台、来电等原因），因此加入失败 |
| -1000 |  | 系统错误 |

Incorrect translation.