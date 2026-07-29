媒体/视频/VideoContext/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext) VideoContext
> 相关文档: [video 组件](https://developers.weixin.qq.com/miniprogram/dev/component/video.html)
VideoContext 实例，可通过 [wx.createVideoContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/wx.createVideoContext.html) 获取。
[VideoContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html) 通过 `id` 跟一个 [video](https://developers.weixin.qq.com/miniprogram/dev/component/video.html) 组件绑定，操作对应的 [video](https://developers.weixin.qq.com/miniprogram/dev/component/video.html) 组件。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#%E6%96%B9%E6%B3%95) 方法
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-play) [VideoContext.play()](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.play.html)
播放视频
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-pause) [VideoContext.pause()](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.pause.html)
暂停视频
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-stop) [VideoContext.stop()](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.stop.html)
停止视频
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-seek-number-position) [VideoContext.seek(number position)](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.seek.html)
跳转到指定位置
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-sendDanmu-Object-data) [VideoContext.sendDanmu(Object data)](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.sendDanmu.html)
发送弹幕
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-playbackRate-number-rate) [VideoContext.playbackRate(number rate)](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.playbackRate.html)
设置倍速播放
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-requestFullScreen-Object-object) [VideoContext.requestFullScreen(Object object)](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.requestFullScreen.html)
进入全屏。若有自定义内容需在全屏时展示，需将内容节点放置到 video 节点内。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-exitFullScreen) [VideoContext.exitFullScreen()](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.exitFullScreen.html)
退出全屏
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-showStatusBar) [VideoContext.showStatusBar()](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.showStatusBar.html)
显示状态栏，仅在iOS全屏下有效
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-hideStatusBar) [VideoContext.hideStatusBar()](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.hideStatusBar.html)
隐藏状态栏，仅在iOS全屏下有效
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-exitPictureInPicture) [VideoContext.exitPictureInPicture()](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.exitPictureInPicture.html)
退出小窗，该方法可在任意页面调用
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-requestBackgroundPlayback) [VideoContext.requestBackgroundPlayback()](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.requestBackgroundPlayback.html)
进入后台小窗播放模式。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-exitBackgroundPlayback) [VideoContext.exitBackgroundPlayback()](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.exitBackgroundPlayback.html)
退出后台小窗播放模式。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-startCasting) [VideoContext.startCasting()](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.startCasting.html)
开始投屏, 拉起半屏搜索设备。仅支持在 tap 事件回调内调用。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-switchCasting) [VideoContext.switchCasting()](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.switchCasting.html)
切换投屏设备。仅支持在 tap 事件回调内调用。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-reconnectCasting) [VideoContext.reconnectCasting()](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.reconnectCasting.html)
重连投屏设备。仅支持在 tap 事件回调内调用。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#VideoContext-exitCasting) [VideoContext.exitCasting()](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.exitCasting.html)
退出投屏。仅支持在 tap 事件回调内调用。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
[在开发者工具中预览效果](https://developers.weixin.qq.com/s/X5V6Xmmk6xYB "在开发者工具中预览效果")
```html
[](http://wxsnsdy.tc.qq.com/105/20210/snsdyvideodownload?filekey=30280201010421301f0201690402534804102ca905ce620b1241b726bc41dcff44e00204012882540400&bizid=1023&hy=SH&fileparam=302c020101042530230204136ffd93020457e3c4ff02024ef202031e8d7f02030f42400204045a320a0201000400)

发送弹幕
```
```js
function getRandomColor () {
let rgb = []
for (let i = 0 ; i < 3; ++i) {
let color = Math.floor(Math.random() \* 256).toString(16)
color = color.length == 1 ? '0' + color : color
rgb.push(color)
}
return '#' + rgb.join('')
}
Page({
onReady (res) {
this.videoContext = wx.createVideoContext('myVideo')
},
inputValue: '',
bindInputBlur (e) {
this.inputValue = e.detail.value
},
bindSendDanmu () {
this.videoContext.sendDanmu({
text: this.inputValue,
color: getRandomColor()
})
}
})
```