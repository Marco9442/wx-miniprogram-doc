# [#](#live-pusher) live-pusher

> 基础库 1.7.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.3.0](../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [wx.createLivePusherContext](../api/media/live/wx.createLivePusherContext.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

实时音视频录制（v2.9.1 起支持[同层渲染](native-component.html#原生组件同层渲染)）。需要[用户授权](../framework/open-ability/authorize.html) `scope.camera`、`scope.record`。

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
|  | url | string |  | 否 | 推流地址。目前仅支持 `rtmp` 格式 | [1.7.0](../framework/compatibility.html) |
|  | mode | string | RTC | 否 | 模式 | [1.7.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | QVGA | Quarter VGA | [3.5.0](../framework/compatibility.html) | | HVGA | Half-size VGA | [3.5.0](../framework/compatibility.html) | | SD | 标清 | [1.7.0](../framework/compatibility.html) | | HD | 高清 | [1.7.0](../framework/compatibility.html) | | FHD | 超清 | [1.7.0](../framework/compatibility.html) | | RTC | 实时通话 | [1.7.0](../framework/compatibility.html) | | | | | | |
|  | autopush | boolean | false | 否 | 自动推流 | [1.7.0](../framework/compatibility.html) |
|  | enableVideoCustomRender | boolean | false | 否 | 自定义渲染，允许开发者自行处理所采集的视频帧，详见[LivePusherContext](../api/media/live/LivePusherContext.html) | [2.29.0](../framework/compatibility.html) |
|  | muted | boolean | false | 否 | 是否静音。即将废弃，可用 `enable-mic` 替代 | [1.7.0](../framework/compatibility.html) |
|  | enable-camera | boolean | true | 否 | 开启摄像头 | [1.7.0](../framework/compatibility.html) |
|  | auto-focus | boolean | true | 否 | 自动聚集 | [1.7.0](../framework/compatibility.html) |
|  | orientation | string | vertical | 否 | 画面方向 | [1.7.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | vertical | 竖直 | | horizontal | 水平 | | | | | | |
|  | beauty | number | 0 | 否 | 美颜，取值范围 0-9 ，0 表示关闭。鸿蒙 OS 暂不支持 | [1.7.0](../framework/compatibility.html) |
|  | whiteness | number | 0 | 否 | 美白，取值范围 0-9 ，0 表示关闭 | [1.7.0](../framework/compatibility.html) |
|  | aspect | string | 9:16 | 否 | 宽高比，可选值有 `3:4`, `9:16` | [1.7.0](../framework/compatibility.html) |
|  | min-bitrate | number | 200 | 否 | 最小码率 | [1.7.0](../framework/compatibility.html) |
|  | max-bitrate | number | 1000 | 否 | 最大码率 | [1.7.0](../framework/compatibility.html) |
|  | audio-quality | string | high | 否 | 高音质(48KHz)或低音质(16KHz)，值为`high`, `low` | [1.7.0](../framework/compatibility.html) |
|  | waiting-image | string |  | 否 | 进入后台时推流的等待画面 | [1.7.0](../framework/compatibility.html) |
|  | waiting-image-hash | string |  | 否 | 等待画面资源的MD5值 | [1.7.0](../framework/compatibility.html) |
|  | zoom | boolean | false | 否 | 调整焦距 | [2.1.0](../framework/compatibility.html) |
|  | device-position | string | front | 否 | 前置或后置，值为`front`, `back` | [2.3.0](../framework/compatibility.html) |
|  | background-mute | boolean | false | 否 | 进入后台时是否静音（已废弃，默认退后台静音） | [1.7.0](../framework/compatibility.html) |
|  | mirror | boolean | false | 否 | 设置推流画面是否镜像，产生的效果在 live-player 反应到 | [2.7.0](../framework/compatibility.html) |
|  | remote-mirror | boolean | false | 否 | 同 mirror 属性，后续 mirror 将废弃 | [2.10.0](../framework/compatibility.html) |
|  | local-mirror | string | auto | 否 | 控制本地预览画面是否镜像 | [2.10.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | auto | 前置摄像头镜像，后置摄像头不镜像 | | enable | 前后置摄像头均镜像 | | disable | 前后置摄像头均不镜像 | | | | | | |
|  | audio-reverb-type | number | 0 | 否 | 音频混响类型 | [2.10.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | 0 | 关闭 | | 1 | KTV | | 2 | 小房间 | | 3 | 大会堂 | | 4 | 低沉 | | 5 | 洪亮 | | 6 | 金属声 | | 7 | 磁性 | | | | | | |
|  | enable-mic | boolean | true | 否 | 开启或关闭麦克风 | [2.10.0](../framework/compatibility.html) |
|  | enable-agc | boolean | false | 否 | 是否开启音频自动增益 | [2.10.0](../framework/compatibility.html) |
|  | enable-ans | boolean | false | 否 | 是否开启音频噪声抑制 | [2.10.0](../framework/compatibility.html) |
|  | audio-volume-type | string | auto | 否 | 音量类型 | [2.10.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | auto | 自动 | | media | 媒体音量 | | voicecall | 通话音量 | | | | | | |
|  | video-width | number | 360 | 否 | 上推的视频流的分辨率宽度 | [2.10.0](../framework/compatibility.html) |
|  | video-height | number | 640 | 否 | 上推的视频流的分辨率高度 | [2.10.0](../framework/compatibility.html) |
|  | beauty-style | string | smooth | 否 | 设置美颜类型。鸿蒙 OS 暂不支持 | [2.12.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | smooth | 光滑美颜 | | nature | 自然美颜 | | | | | | |
|  | filter | string | standard | 否 | 设置色彩滤镜 | [2.12.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | standard | 标准 | | pink | 粉嫩 | | nostalgia | 怀旧 | | blues | 蓝调 | | romantic | 浪漫 | | cool | 清凉 | | fresher | 清新 | | solor | 日系 | | aestheticism | 唯美 | | whitening | 美白 | | cerisered | 樱红 | | | | | | |
|  | picture-in-picture-mode | string/Array |  | 否 | 设置小窗模式： push, pop，空字符串或通过数组形式设置多种模式（如： ["push", "pop"]） | [2.25.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | [] | 取消小窗 | | push | 路由 push 时触发小窗 | | pop | 路由 pop 时触发小窗 | | | | | | |
|  | voice-changer-type | number | 0 | 否 | 0：关闭变声；1：熊孩子；2：萝莉；3：大叔；4：重金属；6：外国人；7：困兽；8：死肥仔；9：强电流；10：重机械；11：空灵 | [2.31.0](../framework/compatibility.html) |
|  | custom-effect | boolean | false | 否 | 是否启动自定义特效，设定后不能更改 | [2.29.1](../framework/compatibility.html) |
|  | skin-whiteness | number | 0 | 否 | 自定义特效美白效果，取值 0~1。需要开启 `custom-effect` | [2.29.1](../framework/compatibility.html) |
|  | skin-smoothness | number | 0 | 否 | 自定义特效磨皮效果，取值 0~1。需要开启 `custom-effect` | [2.29.1](../framework/compatibility.html) |
|  | face-thinness | number | 0 | 否 | 自定义特效瘦脸效果，取值 0~1。需要开启 `custom-effect` | [2.29.1](../framework/compatibility.html) |
|  | eye-bigness | number | 0 | 否 | 自定义特效大眼效果，取值 0~1。需要开启 `custom-effect` | [2.29.1](../framework/compatibility.html) |
|  | fps | number | 15 | 否 | 帧率，有效值为 1~30 | [2.31.0](../framework/compatibility.html) |
|  | mute-on-audio-conflict | boolean | false | 否 | 音频冲突时是否静音 | [3.16.2](../framework/compatibility.html) |
|  | bindstatechange | eventhandle |  | 否 | 状态变化事件，detail = {code} | [1.7.0](../framework/compatibility.html) |
|  | bindnetstatus | eventhandle |  | 否 | 网络状态通知，detail = {info} | [1.9.0](../framework/compatibility.html) |
|  | binderror | eventhandle |  | 否 | 渲染错误事件，detail = {errMsg, errCode} | [1.7.4](../framework/compatibility.html) |
|  | bindbgmstart | eventhandle |  | 否 | 背景音开始播放时触发 | [2.4.0](../framework/compatibility.html) |
|  | bindbgmprogress | eventhandle |  | 否 | 背景音进度变化时触发，detail = {progress, duration} | [2.4.0](../framework/compatibility.html) |
|  | bindbgmcomplete | eventhandle |  | 否 | 背景音播放完成时触发 | [2.4.0](../framework/compatibility.html) |
|  | bindaudiovolumenotify | eventhandle |  | 否 | 返回麦克风采集的音量大小 | [2.12.0](../framework/compatibility.html) |
|  | bindenterpictureinpicture | eventhandler |  | 否 | 进入小窗 | [2.25.0](../framework/compatibility.html) |
|  | bindleavepictureinpicture | eventhandler |  | 否 | 退出小窗 | [2.25.0](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`：开发者工具上暂不支持。
2. `tip`：[live-pusher](live-pusher.html) 默认宽度为100%、无默认高度，请通过wxss设置宽高。
3. `tip`：`waiting-image` 属性在 2.3.0 起完整支持网络路径、临时文件和包内路径。
4. `tip`：请注意[原生组件使用限制](./native-component.html#原生组件的使用限制)。
5. `tip`: 相关介绍和原理可参考[此文章](https://developers.weixin.qq.com/community/develop/doc/000cccb57444107426c621b1756c09)

## [#](#错误码（errCode）) 错误码（errCode）

| 代码 | 说明 |
| --- | --- |
| 10001 | 用户禁止使用摄像头 |
| 10002 | 用户禁止使用录音 |
| 10003 | 背景音资源（BGM）加载失败 |
| 10004 | 等待画面资源（waiting-image）加载失败 |

## [#](#状态码（code）) 状态码（code）

| 代码 | 说明 |
| --- | --- |
| 1001 | 推流：已经连接推流服务器 |
| 1002 | 推流：已经与服务器握手完毕，开始推流 |
| 1003 | 推流：打开摄像头成功 |
| 1004 | 推流：录屏启动成功 |
| 1005 | 推流：推流动态调整分辨率 |
| 1006 | 推流：推流动态调整码率 |
| 1007 | 推流：首帧画面采集完成 |
| 1008 | 推流：编码器启动 |
| 1009 | 推流：发送视频首帧 |
| 1018 | 推流：进房成功（ROOM协议特有） |
| 1019 | 推流：退房成功（ROOM协议特有） |
| 1020 | 推流：远端主播列表变化（ROOM协议特有） |
| 1021 | 推流：网络变更时重进房，WiFi 切换到4G 会触发断线重连（ROOM协议特有） |
| 1022 | 推流：进入房间失败（ROOM协议特有） |
| 1031 | 推流：远端主播进房通知（ROOM协议特有） |
| 1032 | 推流：远端主播退房通知（ROOM协议特有） |
| 1033 | 推流：远端主播视频状态位变化（ROOM协议特有） |
| 1034 | 推流：远端主播音频状态位变化（ROOM协议特有） |
| 1101 | 推流：网络状况不佳：上行带宽太小，上传数据受阻 |
| 1102 | 推流：网络断连, 已启动自动重连 |
| 1103 | 推流：硬编码启动失败，内部会尝试切换软编码器（Android特有） |
| 1104 | 推流：编码器类型发生变化 |
| 1109 | 推流：软编码启动失败, 内部会尝试切换硬编码器（Android特有） |
| 2027 | 推流：麦克风启动成功 |
| 3001 | 推流：RTMP DNS解析失败 |
| 3002 | 推流：RTMP服务器连接失败 |
| 3003 | 推流：RTMP服务器握手失败 |
| 3004 | 推流：RTMP服务器主动断开，请检查推流地址的合法性或防盗链有效期 |
| 3005 | 推流：RTMP 读/写失败 |
| -1301 | 推流：打开摄像头失败 |
| -1302 | 推流：打开麦克风失败 |
| -1303 | 推流：视频编码失败 |
| -1304 | 推流：音频编码失败 |
| -1305 | 推流：不支持的视频分辨率 |
| -1306 | 推流：不支持的音频采样率 |
| -1307 | 推流：网络断连，且经多次重连抢救无效，请自行重启推流 |
| -1308 | 推流：开始录屏失败，可能是被用户拒绝 |
| -1309 | 推流：录屏失败，不支持的Android系统版本，需要5.0以上的系统 |
| -1310 | 推流：录屏被其他应用打断了 |
| -1311 | 推流：Android Mic打开成功，但是录不到音频数据 |
| -1312 | 推流：录屏动态切横竖屏失败 |
| -1318 | 推流：麦克风设置参数失败，当前设备不支持设置的参数 |
| 10001 | 用户禁止使用摄像头 |
| 10002 | 用户禁止使用录音 |
| 10003 | 背景音资源（BGM）加载失败 |
| 10004 | 等待画面资源（waiting-image）加载失败 |
| 4998 | Mic状态切换的时候，enable-mic触发（iOS特有） |
| 4999 | mute状态切换的时候，muted 触发（iOS特有） |
| 5000 | 推流：被挂起，小程序或微信被退后台时挂起推流 |
| 5001 | 系统电话打断或者微信音视频电话打断 |
| 0 | 无错误 |

## [#](#网络状态数据（info）) 网络状态数据（info）

| 键名 | 说明 |
| --- | --- |
| videoBitrate | 当前视频编/码器输出的比特率，单位 kbps |
| audioBitrate | 当前音频编/码器输出的比特率，单位 kbps |
| videoFPS | 当前视频帧率 |
| videoGOP | 当前视频 GOP,也就是每两个关键帧(I帧)间隔时长，单位 s |
| netSpeed | 当前的发送/接收速度 |
| netJitter | 网络抖动情况，抖动越大，网络越不稳定 |
| netQualityLevel | 网络质量：0：未定义 1：最好 2：好 3：一般 4：差 5：很差 6：不可用 |
| videoWidth | 视频画面的宽度 |
| videoHeight | 视频画面的高度 |
| videoCache | 主播端堆积的视频帧数 |
| audioCache | 主播端堆积的音频帧数 |

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/KvWD9mmA62Yk "在开发者工具中预览效果")

```
  <live-pusher url="https://domain/push_stream" mode="RTC" autopush bindstatechange="statechange" style="width: 300px; height: 225px;" />
```

```
Page({
  statechange(e) {
    console.log('live-pusher code:', e.detail.code)
  }
})
```

Incorrect translation.