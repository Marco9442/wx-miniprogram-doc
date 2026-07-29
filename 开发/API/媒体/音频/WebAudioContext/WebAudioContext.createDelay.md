媒体/音频/WebAudioContext/WebAudioContext.createDelay/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/WebAudioContext.createDelay.html\#DelayNode-WebAudioContext-createDelay-number-maxDelayTime) DelayNode WebAudioContext.createDelay(number maxDelayTime)
> \*\*小程序插件\*\*：不支持
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/WebAudioContext.createDelay.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
创建一个DelayNode
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/WebAudioContext.createDelay.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/WebAudioContext.createDelay.html\#number-maxDelayTime) number maxDelayTime
最大延迟时间
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/WebAudioContext.createDelay.html\#%E8%BF%94%E5%9B%9E%E5%80%BC) 返回值
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/WebAudioContext.createDelay.html\#DelayNode) DelayNode
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/WebAudioContext.createDelay.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
示例代码
```javascript
let audioCtx = wx.createWebAudioContext()
const delayNode = audioCtx.createDelay(5)
```