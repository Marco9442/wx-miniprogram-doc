媒体/音频/InnerAudioContext/InnerAudioContext.offPause/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/InnerAudioContext.offPause.html\#InnerAudioContext-offPause-function-listener) InnerAudioContext.offPause(function listener)
> 基础库 1.9.0 开始支持，低版本需做 [兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。
> \*\*小程序插件\*\*：支持
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/InnerAudioContext.offPause.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
移除音频暂停事件的监听函数
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/InnerAudioContext.offPause.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/InnerAudioContext.offPause.html\#function-listener) function listener
onPause 传入的监听函数。不传此参数则移除所有监听函数。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/InnerAudioContext.offPause.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
```js
const listener = function (res) { console.log(res) }
InnerAudioContext.onPause(listener)
InnerAudioContext.offPause(listener) // 需传入与监听时同一个的函数对象
```