# [#](#video) video

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [wx.createVideoContext](../api/media/video/wx.createVideoContext.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

视频（v2.4.0 起支持[同层渲染](native-component.html#原生组件同层渲染)）。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | src | string |  | 是 | 要播放视频的资源地址，支持网络路径、本地临时路径、云文件ID（[2.3.0](../framework/compatibility.html)） | [1.0.0](../framework/compatibility.html) |
|  | duration | number |  | 否 | 指定视频时长 | [1.1.0](../framework/compatibility.html) |
|  | controls | boolean | true | 否 | 是否显示默认播放控件（播放/暂停按钮、播放进度、时间） | [1.0.0](../framework/compatibility.html) |
|  | danmu-list | Array.<object> |  | 否 | 弹幕列表 | [1.0.0](../framework/compatibility.html) |
|  | danmu-btn | boolean | false | 否 | 是否显示弹幕按钮，只在初始化时有效，不能动态变更 | [1.0.0](../framework/compatibility.html) |
|  | enable-danmu | boolean | false | 否 | 是否展示弹幕，只在初始化时有效，不能动态变更 | [1.0.0](../framework/compatibility.html) |
|  | autoplay | boolean | false | 否 | 是否自动播放 | [1.0.0](../framework/compatibility.html) |
|  | loop | boolean | false | 否 | 是否循环播放 | [1.4.0](../framework/compatibility.html) |
|  | muted | boolean | false | 否 | 是否静音播放 | [1.4.0](../framework/compatibility.html) |
|  | initial-time | number | 0 | 否 | 指定视频初始播放位置 | [1.6.0](../framework/compatibility.html) |
|  | page-gesture | boolean | false | 否 | 在非全屏模式下，是否开启亮度与音量调节手势（废弃，见 vslide-gesture） | [1.6.0](../framework/compatibility.html) |
|  | direction | number |  | 否 | 设置全屏时视频的方向，不指定则根据宽高比自动判断 | [1.7.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | 0 | 正常竖向 | | 90 | 屏幕逆时针90度 | | -90 | 屏幕顺时针90度 | | | | | | |
|  | show-progress | boolean | true | 否 | 若不设置，宽度大于240时才会显示 | [1.9.0](../framework/compatibility.html) |
|  | show-fullscreen-btn | boolean | true | 否 | 是否显示全屏按钮 | [1.9.0](../framework/compatibility.html) |
|  | show-play-btn | boolean | true | 否 | 是否显示视频底部控制栏的播放按钮 | [1.9.0](../framework/compatibility.html) |
|  | show-center-play-btn | boolean | true | 否 | 是否显示视频中间的播放按钮 | [1.9.0](../framework/compatibility.html) |
|  | enable-progress-gesture | boolean | true | 否 | 是否开启控制进度的手势 | [1.9.0](../framework/compatibility.html) |
|  | object-fit | string | contain | 否 | 当视频大小与 video 容器大小不一致时，视频的表现形式 | [1.0.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | contain | 包含 | | fill | 填充 | | cover | 覆盖 | | | | | | |
|  | poster | string |  | 否 | 视频封面的图片网络资源地址或云文件ID（[2.3.0](../framework/compatibility.html)）。若 controls 属性值为 false 则设置 poster 无效 | [1.0.0](../framework/compatibility.html) |
|  | show-mute-btn | boolean | false | 否 | 是否显示静音按钮 | [2.4.0](../framework/compatibility.html) |
|  | title | string |  | 否 | 视频的标题，全屏时在顶部展示 | [2.4.0](../framework/compatibility.html) |
|  | play-btn-position | string | bottom | 否 | 播放按钮的位置 | [2.4.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | bottom | controls bar上 | | center | 视频中间 | | | | | | |
|  | enable-play-gesture | boolean | false | 否 | 是否开启播放手势，即双击切换播放/暂停 | [2.4.0](../framework/compatibility.html) |
|  | auto-pause-if-navigate | boolean | true | 否 | 当跳转到本小程序的其他页面时，是否自动暂停本页面的视频播放 | [2.5.0](../framework/compatibility.html) |
|  | auto-pause-if-open-native | boolean | true | 否 | 当跳转到其它微信原生页面时，是否自动暂停本页面的视频 | [2.5.0](../framework/compatibility.html) |
|  | vslide-gesture | boolean | false | 否 | 在非全屏模式下，是否开启亮度与音量调节手势（同 page-gesture） | [2.6.2](../framework/compatibility.html) |
|  | vslide-gesture-in-fullscreen | boolean | true | 否 | 在全屏模式下，是否开启亮度与音量调节手势 | [2.6.2](../framework/compatibility.html) |
|  | show-bottom-progress | boolean | true | 否 | 是否展示底部进度条 | [2.8.0](../framework/compatibility.html) |
|  | ad-unit-id | string |  | 是 | 视频前贴广告单元ID，更多详情可参考开放能力[视频前贴广告](../framework/open-ability/ad/video-patch-ad.html) | [2.8.1](../framework/compatibility.html) |
|  | poster-for-crawler | string |  | 是 | 用于给搜索等场景作为视频封面展示，建议使用无播放 icon 的视频封面图，只支持网络地址 |  |
|  | show-casting-button | boolean | false | 否 | 显示投屏按钮。安卓在同层渲染下生效，支持 DLNA 协议；iOS 支持 AirPlay 和 DLNA 协议；鸿蒙 OS 暂不支持。可以通过[VideoContext](../api/media/video/VideoContext.html)的相关方法进行操作。 | [2.10.2](../framework/compatibility.html) |
|  | picture-in-picture-mode | string/Array |  | 否 | 设置小窗模式： push, pop，空字符串或通过数组形式设置多种模式（如： ["push", "pop"]）。鸿蒙 OS 暂不支持 | [2.11.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | [] | 取消小窗 | | push | 路由 push 时触发小窗 | | pop | 路由 pop 时触发小窗 | | | | | | |
|  | picture-in-picture-show-progress | boolean | false | 否 | 是否在小窗模式下显示播放进度 | [2.11.0](../framework/compatibility.html) |
|  | picture-in-picture-init-position | string |  | 否 | 小窗模式下小窗的初始显示位置，格式为 (alignment, y)，其中 alignment 表示小窗吸附屏幕左侧还是右侧，可选值为 left、right，y 代表小窗最顶部所在的屏幕高度百分比 | [3.3.0](../framework/compatibility.html) |
|  | enable-system-pip | boolean | true | 否 | 是否支持 iOS 系统画中画，默认支持 | [3.15.1](../framework/compatibility.html) |
|  | enable-auto-rotation | boolean | false | 否 | 是否开启手机横屏时自动全屏，当系统设置开启自动旋转时生效 | [2.11.0](../framework/compatibility.html) |
|  | show-screen-lock-button | boolean | false | 否 | 是否显示锁屏按钮，仅在全屏时显示，锁屏后控制栏的操作 | [2.11.0](../framework/compatibility.html) |
|  | show-snapshot-button | boolean | false | 否 | 是否显示截屏按钮，仅在全屏时显示 | [2.13.0](../framework/compatibility.html) |
|  | show-background-playback-button | boolean | true | 否 | 是否展示后台小窗播放按钮。鸿蒙 OS 暂不支持。基础库 3.6.0 开始默认值为 true。 | [2.14.3](../framework/compatibility.html) |
|  | background-poster | string |  | 否 | 进入后台小窗播放后的通知栏图标（Android 独有） | [2.14.3](../framework/compatibility.html) |
|  | referrer-policy | string | no-referrer | 否 | 格式固定为 `https://servicewechat.com/{appid}/{version}/page-frame.html`，其中 {appid} 为小程序的 appid，{version} 为小程序的版本号，版本号为 0 表示为开发版、体验版以及审核版本，版本号为 devtools 表示为开发者工具，其余为正式版本； | [2.13.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | origin | 发送完整的referrer | | no-referrer | 不发送 | | | | | | |
|  | is-drm | boolean |  | 否 | 是否为 DRM 视频源 | [2.19.3](../framework/compatibility.html) |
|  | is-live | boolean |  | 否 | 是否为直播源 | [2.28.1](../framework/compatibility.html) |
|  | provision-url | string |  | 否 | DRM 设备身份认证 url，仅 is-drm 为 true 时生效 (Android) | [2.19.3](../framework/compatibility.html) |
|  | certificate-url | string |  | 否 | DRM 设备身份认证 url，仅 is-drm 为 true 时生效 (iOS) | [2.19.3](../framework/compatibility.html) |
|  | license-url | string |  | 否 | DRM 获取加密信息 url，仅 is-drm 为 true 时生效 | [2.19.3](../framework/compatibility.html) |
|  | preferred-peak-bit-rate | number |  | 否 | 指定码率上界，单位为比特每秒 | [2.26.0](../framework/compatibility.html) |
|  | bindplay | eventhandle |  | 否 | 当开始/继续播放时触发play事件 | [1.0.0](../framework/compatibility.html) |
|  | bindpause | eventhandle |  | 否 | 当暂停播放时触发 pause 事件 | [1.0.0](../framework/compatibility.html) |
|  | bindended | eventhandle |  | 否 | 当播放到末尾时触发 ended 事件 | [1.0.0](../framework/compatibility.html) |
|  | bindtimeupdate | eventhandle |  | 否 | 播放进度变化时触发，event.detail = {currentTime, duration} 。触发频率 250ms 一次 | [1.0.0](../framework/compatibility.html) |
|  | bindfullscreenchange | eventhandle |  | 否 | 视频进入和退出全屏时触发，event.detail = {fullScreen, direction}，direction 有效值为 vertical 或 horizontal | [1.4.0](../framework/compatibility.html) |
|  | bindwaiting | eventhandle |  | 否 | 视频出现缓冲时触发 | [1.7.0](../framework/compatibility.html) |
|  | binderror | eventhandle |  | 否 | 视频播放出错时触发 | [1.7.0](../framework/compatibility.html) |
|  | bindprogress | eventhandle |  | 否 | 加载进度变化时触发，只支持一段加载。event.detail = {buffered}，百分比 | [2.4.0](../framework/compatibility.html) |
|  | bindloadedmetadata | eventhandle |  | 否 | 视频元数据加载完成时触发。event.detail = {width, height, duration} | [2.7.0](../framework/compatibility.html) |
|  | bindcontrolstoggle | eventhandle |  | 否 | 切换 controls 显示隐藏时触发。event.detail = {show} | [2.9.5](../framework/compatibility.html) |
|  | bindenterpictureinpicture | eventhandler |  | 否 | 播放器进入小窗 | [2.11.0](../framework/compatibility.html) |
|  | bindleavepictureinpicture | eventhandler |  | 否 | 播放器退出小窗 | [2.11.0](../framework/compatibility.html) |
|  | bindseekcomplete | eventhandler |  | 否 | seek 完成时触发 (position iOS 单位 s, Android 单位 ms) | [2.12.0](../framework/compatibility.html) |
|  | bindcastinguserselect | eventhandler |  | 否 | 用户选择投屏设备时触发 detail = { state: "success"/"fail" }。鸿蒙 OS 暂不支持 | [2.32.0](../framework/compatibility.html) |
|  | bindcastingstatechange | eventhandler |  | 否 | 投屏成功/失败时触发 detail = { type, state: "success"/"fail" }。鸿蒙 OS 暂不支持 | [2.32.0](../framework/compatibility.html) |
|  | bindcastinginterrupt | eventhandler |  | 否 | 投屏被中断时触发。鸿蒙 OS 暂不支持 | [2.32.0](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`：`[video](video.html) 默认宽度 300px、高度 225px，可通过 wxss 设置宽高。
2. `tip`：从 2.4.0 起 video 支持同层渲染，更多请参考[原生组件使用限制](native-component.html#原生组件的使用限制)
3. `tip`: 若当前组件所在的页面或全局开启了 `enablePassiveEvent` 配置项，该内置组件可能会出现非预期表现（详情参考 [enablePassiveEvent 文档](../reference/configuration/app)）

## [#](#支持的格式) 支持的格式

| 格式 | iOS | Android |
| --- | --- | --- |
| mp4 | √ | √ |
| mov | √ | x |
| m4v | √ | x |
| 3gp | √ | √ |
| avi | √ | x |
| m3u8 | √ | √ |
| webm | x | √ |

## [#](#支持的编码格式) 支持的编码格式

| 格式 | iOS | Android |
| --- | --- | --- |
| H.264 | √ | √ |
| HEVC | √ | √ |
| MPEG-4 | √ | √ |
| VP9 | x | √ |

## [#](#小窗特性说明) 小窗特性说明

video 小窗支持以下三种触发模式（在组件上设置 picture-in-picture-mode 属性）：

1. push 模式，即从当前页跳转至下一页时出现小窗（页面栈push）
2. pop 模式，即离开当前页面时触发（页面栈pop）
3. 以上两种路由行为均触发小窗

此外，小窗还支持以下特性：

- 小窗容器尺寸会根据原组件尺寸自动判断
- 点击小窗，用户会被导航回小窗对应的播放器页面
- 小窗出现后，用户可点击小窗右上角的关闭按钮或调用 context.exitPictureInPicture() 接口关闭小窗

当播放器进入小窗模式后，播放器所在页面处于 hide 状态(触发 onHide 生命周期)，该页面不会被销毁。当小窗被关闭时，播放器所在页面会被 unload (触发 onUnload 生命周期)。

## [#](#DRM-加密播放) DRM 加密播放

1. 小程序开发者获取到 DRM 加密的 视频地址、身份认证 url、license url
2. 使用 video 标签将以上几个参数填入
3. 小程序确认该 video 为 DRM 视频源，进行 DRM 设备身份认证并且获取播放许可证
4. 设备身份认证通过并获取播放许可证之后，由 DRM 底层进行解密播放

![](https://res.wx.qq.com/op_res/XVj4asvwuQWYAY1l-nwGbIm5s8cmEyyOvXrGqRLImfTYKKbsPldNdE5vBt0gshXeJn-tfR62AjjdVbF0MisXaA)

### [#](#Q-A) Q&A

Q：为什么设备身份认证 url 要区分 Android 和 iOS ？

A：由于 Android 和 iOS 是基于不同的 DRM 协议，Android：widevine；iOS：fairplay，所以身份认证这块有所不同，需要分别提供身份认证 url。

Q：license url 的格式是什么样的？

A：目前 license url 需要支持标准 license 回包，即裸 license

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/X5V6Xmmk6xYB "在开发者工具中预览效果")

Incorrect translation.