# [#](#live-player) live-player

> 基础库 1.7.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.3.0](../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [wx.createLivePlayerContext](../api/media/live/wx.createLivePlayerContext.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

实时音视频播放（v2.9.1 起支持[同层渲染](native-component.html#原生组件同层渲染)）。

## [#](#申请开通) 申请开通

暂只针对以下类目的小程序开放，需要先通过类目审核，再在小程序管理后台，「开发」-「接口设置」中自助开通该组件权限。

| 一级类目/主体类型 | 二级类目 | 小程序内容场景 |
| --- | --- | --- |
| 社交 | 直播 | 涉及非表演类在线直播（如电商类、教育类等）等。选择该类目后首次提交代码审核，需经当地互联网主管机关审核确认，预计审核时长 7 天左右 |
| 社交 | 直播表演 | 适用于提供表演类在线直播（如游戏直播、娱乐秀场类、线上演唱会、剧目直播、演艺直播等）。选择该类目后首次提交代码审核，需经当地互联网主管机关审核确认，预计审核时长 7 天左右 |
| 教育 | 在线视频课程 | 网课、在线培训、讲座等教育类直播 |
| 医疗 | 互联网医院，公立医疗机构，三级私立医疗机构，其他私立医疗机构 | 问诊、大型健康讲座等直播 |
| 金融 | 银行、信托、公募基金、私募基金、证券/期货、证券、期货投资咨询、保险、企业征信、新三板信息服务平台、股票信息服务平台、股票信息服务平台（港股/美股）、消费金融、融资担保、汽车金融/融资租赁 | 金融产品视频客服理赔、金融产品推广直播等 |
| 汽车 | 汽车预售 | 汽车预售、推广直播 |
| 政府主体账号 | / | 政府相关工作推广直播、领导讲话直播等 |
| IT科技 | 多方通信；音视频设备 | 为多方提供电话会议/视频会议等服务；智能家居场景下控制摄像头 |
| 房地产服务 | 房地产营销 | 房地产营销直播服务、在线音视频带看等 |
| 商业服务 | 公证 | 在线业务办理等 |
| 公共服务 | 交通运输 | 仅适用于港澳特区政府主体提供当地的交通管理相关政务服务（如道路运输、车辆管理等） |

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | src | string |  | 否 | 音视频地址。目前仅支持 `flv`, `rtmp` 格式 | [1.7.0](../framework/compatibility.html) |
|  | mode | string | live | 否 | 模式 | [1.7.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | live | 直播 | | RTC | 实时通话，该模式时延更低 | | | | | | |
|  | autoplay | boolean | false | 否 | 自动播放 | [1.7.0](../framework/compatibility.html) |
|  | muted | boolean | false | 否 | 是否静音 | [1.7.0](../framework/compatibility.html) |
|  | orientation | string | vertical | 否 | 画面方向 | [1.7.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | vertical | 竖直 | | horizontal | 水平 | | | | | | |
|  | object-fit | string | contain | 否 | 填充模式，可选值有 `contain`，`fillCrop` | [1.7.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | contain | 图像长边填满屏幕，短边区域会被填充⿊⾊ | | fillCrop | 图像铺满屏幕，超出显示区域的部分将被截掉 | | | | | | |
|  | background-mute | boolean | false | 否 | 进入后台时是否静音（已废弃，默认退后台静音） | [1.7.0](../framework/compatibility.html) |
|  | min-cache | number | 1 | 否 | 最小缓冲区，单位s（RTC 模式推荐 0.2s） | [1.7.0](../framework/compatibility.html) |
|  | max-cache | number | 3 | 否 | 最大缓冲区，单位s（RTC 模式推荐 0.8s）。缓冲区用来抵抗网络波动，缓冲数据越多，网络抗性越好，但时延越大。 | [1.7.0](../framework/compatibility.html) |
|  | sound-mode | string | speaker | 否 | 声音输出方式 | [1.9.90](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | speaker | 扬声器 | | ear | 听筒 | | | | | | |
|  | auto-pause-if-navigate | boolean | true | 否 | 当跳转到本小程序的其他页面时，是否自动暂停本页面的实时音视频播放 | [2.5.0](../framework/compatibility.html) |
|  | auto-pause-if-open-native | boolean | true | 否 | 当跳转到其它微信原生页面时，是否自动暂停本页面的实时音视频播放 | [2.5.0](../framework/compatibility.html) |
|  | picture-in-picture-mode | string/Array |  | 否 | 设置小窗模式： push, pop，空字符串或通过数组形式设置多种模式（如： ["push", "pop"]） | [2.10.3](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | [] | 取消小窗 | | push | 路由 push 时触发小窗 | | pop | 路由 pop 时触发小窗 | | | | | | |
|  | picture-in-picture-init-position | string |  | 否 | 小窗模式下小窗的初始显示位置，格式为 (alignment, y)，其中 alignment 表示小窗吸附屏幕左侧还是右侧，可选值为 left、right，y 代表小窗最顶部所在的屏幕高度百分比 | [3.3.0](../framework/compatibility.html) |
|  | enable-system-pip | boolean | true | 否 | 是否支持 iOS 系统画中画，默认支持 | [3.14.1](../framework/compatibility.html) |
|  | enable-auto-rotation | boolean | false | 否 | 是否开启手机横屏时自动全屏，当系统设置开启自动旋转时生效 | [2.11.0](../framework/compatibility.html) |
|  | referrer-policy | string | no-referrer | 否 | 格式固定为 `https://servicewechat.com/{appid}/{version}/page-frame.html`，其中 {appid} 为小程序的 appid，{version} 为小程序的版本号，版本号为 0 表示为开发版、体验版以及审核版本，版本号为 devtools 表示为开发者工具，其余为正式版本； | [2.13.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | origin | 发送完整的referrer | | no-referrer | 不发送 | | | | | | |
|  | enable-casting | boolean | false | 否 | 是否支持投屏。开启后，可以通过 [LivePlayerContext](../api/media/live/LivePlayerContext.html) 上相关方法进行操作。 | [2.32.0](../framework/compatibility.html) |
|  | mute-on-audio-conflict | boolean | false | 否 | 音频冲突时是否静音 | [3.16.2](../framework/compatibility.html) |
|  | bindstatechange | eventhandle |  | 否 | 播放状态变化事件，detail = {code} | [1.7.0](../framework/compatibility.html) |
|  | bindfullscreenchange | eventhandle |  | 否 | 全屏变化事件，detail = {direction, fullScreen} | [1.7.0](../framework/compatibility.html) |
|  | bindnetstatus | eventhandle |  | 否 | 网络状态通知，detail = {info} | [1.9.0](../framework/compatibility.html) |
|  | bindaudiovolumenotify | eventhandler |  | 否 | 播放音量大小通知，detail = {} | [2.10.0](../framework/compatibility.html) |
|  | bindenterpictureinpicture | eventhandler |  | 否 | 播放器进入小窗 | [2.11.0](../framework/compatibility.html) |
|  | bindleavepictureinpicture | eventhandler |  | 否 | 播放器退出小窗 | [2.11.0](../framework/compatibility.html) |
|  | bindcastinguserselect | eventhandler |  | 否 | 用户选择投屏设备时触发 detail = { state: "success"/"fail" } | [2.32.0](../framework/compatibility.html) |
|  | bindcastingstatechange | eventhandler |  | 否 | 投屏成功/失败时触发 detail = { type, state: "success"/"fail" } | [2.32.0](../framework/compatibility.html) |
|  | bindcastinginterrupt | eventhandler |  | 否 | 投屏被中断时触发 | [2.32.0](../framework/compatibility.html) |

## [#](#状态码) 状态码

| 代码 | 说明 |
| --- | --- |
| 2001 | 拉流：已经连接服务器 |
| 2002 | 拉流：已经连接服务器，开始拉流 |
| 2003 | 拉流：视频首帧渲染事件 |
| 2004 | 拉流：视频播放开始 |
| 2007 | 拉流：视频播放Loading |
| 2008 | 拉流：视频解码器启动 |
| 2009 | 拉流：视频分辨率改变 |
| 2026 | 拉流：音频播放首帧事件 |
| 2030 | 音频设备发生改变，即当前的输入输出设备发生改变，比如耳机被拔出 |
| 2032 | 拉流：Audio Session 被其他 App 中断（iOS 平台特有） |
| 2033 | 拉流：渲染view窗口变化后首帧渲染事件（比如分辨率发生变化）flv，rtmp标准协议特有，如果期望监听视频首帧渲染事件，建议用2003 |
| 2034 | 拉流：接收首帧视频 |
| 2035 | 拉流：解码首帧视频 |
| 2036 | 拉流：视频时间戳发生回退 |
| 2101 | 拉流：当前视频帧解码失败 |
| 2102 | 拉流：当前音频帧解码失败 |
| 2103 | 拉流：网络连不上，自动重连事件，重连最多尝试3次，自动重连连续失败超过三次会放弃，返回-2301 |
| 2104 | 拉流：网络来包不稳：可能是下行带宽不足，或由于主播端出流不均匀 |
| 2105 | 拉流：当前视频播放出现卡顿 |
| 2106 | 拉流：硬解启动失败，采用软解 |
| 2107 | 拉流：当前视频帧不连续，可能丢帧 |
| 2108 | 拉流：当前流硬解第一个I帧失败，SDK自动切软解 |
| 3001 | 拉流：RTMP-DNS解析失败 |
| 3002 | 拉流：RTMP服务器连接失败 |
| 3003 | 拉流：RTMP服务器握手失败 |
| 3005 | 拉流：RTMP 读/写失败，之后会发起网络重试 |
| -2301 | 拉流：网络断连，且经多次重连无效，请自行重启拉流 |
| -2302 | 拉流：获取拉流地址失败 |
| 0 | 无错误 |
| 6000 | 拉流：被挂起，小程序或微信被退后台时挂起拉流 |

## [#](#网络状态数据) 网络状态数据

| 键名 | 说明 |
| --- | --- |
| videoBitrate | 当前视频编/码器输出的比特率，单位 kbps |
| audioBitrate | 当前音频编/码器输出的比特率，单位 kbps |
| videoFPS | 当前视频帧率 |
| videoGOP | 当前视频 GOP,也就是每两个关键帧(I帧)间隔时长，单位 s |
| netSpeed | 当前的发送/接收速度 |
| netJitter | 网络抖动情况，为 0 时表示没有任何抖动，值越大表明网络抖动越大，网络越不稳定 |
| netQualityLevel | 网络质量：0：未定义 1：最好 2：好 3：一般 4：差 5：很差 6：不可用 |
| videoWidth | 视频画面的宽度 |
| videoHeight | 视频画面的高度 |
| videoCache | 缓冲的视频总时长，单位毫秒 |
| audioCache | 缓冲的音频总时长，单位毫秒 |
| vDecCacheSize | 解码器中缓存的视频帧数 (Android 端硬解码时存在） |
| vSumCacheSize | 缓冲的总视频帧数，该数值越大，播放延迟越高 |
| avPlayInterval | 音画同步错位时间（播放），单位 ms，此数值越小，音画同步越好 |
| avRecvInterval | 音画同步错位时间（网络），单位 ms，此数值越小，音画同步越好 |
| audioCacheThreshold | 音频缓冲时长阈值，缓冲超过该阈值后，播放器会开始调控延时 |

## [#](#小窗特性说明) 小窗特性说明

live-player 小窗支持以下三种触发模式（在组件上设置 picture-in-picture-mode 属性）：

1. push 模式，即从当前页跳转至下一页时出现小窗（页面栈push）
2. pop 模式，即离开当前页面时触发（页面栈pop）
3. 以上两种路由行为均触发小窗

此外，小窗还支持以下特性：

- 小窗容器尺寸会根据原组件尺寸自动判断
- 点击小窗，用户会被导航回小窗对应的播放器页面
- 小窗出现后，用户可点击小窗右上角的关闭按钮或调用 context.exitPictureInPicture() 接口关闭小窗

当播放器进入小窗模式后，播放器所在页面处于 hide 状态(触发 onHide 生命周期)，该页面不会被销毁。当小窗被关闭时，播放器所在页面会被 unload (触发 onUnload 生命周期)。

## [#](#Bug-Tip) Bug & Tip

1. `tip`：[live-player](live-player.html) 默认宽度300px、高度225px，可通过wxss设置宽高。
2. `tip`：开发者工具上暂不支持。
3. `tip`: 相关介绍和原理可参考[此文章](https://developers.weixin.qq.com/community/develop/doc/000cccb57444107426c621b1756c09)

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/UzWEzmm763Y4 "在开发者工具中预览效果")

```
<live-player src="https://domain/pull_stream" mode="RTC" autoplay bindstatechange="statechange" binderror="error" style="width: 300px; height: 225px;" />
```

```
Page({
  statechange(e) {
    console.log('live-player code:', e.detail.code)
  },
  error(e) {
    console.error('live-player error:', e.detail.errMsg)
  }
})
```

Incorrect translation.