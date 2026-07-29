# [#](#wx-playBackgroundAudio-Object-object) wx.playBackgroundAudio(Object object)

从基础库 [1.2.0](../../../framework/compatibility.html) 开始，本接口停止维护，请使用 [wx.getBackgroundAudioManager](wx.getBackgroundAudioManager.html) 代替

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

使用后台播放器播放音乐。对于微信客户端来说，只能同时有一个后台音乐在播放。当用户离开小程序后，音乐将暂停播放；当用户在其他小程序占用了音乐播放器，原有小程序内的音乐将停止播放。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| dataUrl | string |  | 是 | 音乐链接，目前支持的格式有 m4a, aac, mp3, wav |
| title | string |  | 否 | 音乐标题 |
| coverImgUrl | string |  | 否 | 封面URL |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
wx.playBackgroundAudio({
  dataUrl: '',
  title: '',
  coverImgUrl: ''
})
```

Incorrect translation.