# [#](#VideoDecoder) VideoDecoder

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

可通过 [wx.createVideoDecoder](wx.createVideoDecoder.html) 创建。

[VideoDecoder](VideoDecoder.html) 视频解码器，可以进行视频解码相关操作，逐帧获取解码数据

## [#](#方法) 方法

### [#](#Promise-VideoDecoder-start-Object-object) [Promise VideoDecoder.start(Object object)](VideoDecoder.start.html)

开始解码

### [#](#Promise-VideoDecoder-seek-number-position) [Promise VideoDecoder.seek(number position)](VideoDecoder.seek.html)

跳到某个时间点解码

### [#](#Promise-VideoDecoder-stop) [Promise VideoDecoder.stop()](VideoDecoder.stop.html)

停止解码

### [#](#Promise-VideoDecoder-remove) [Promise VideoDecoder.remove()](VideoDecoder.remove.html)

移除解码器

### [#](#Object-VideoDecoder-getFrameData) [Object VideoDecoder.getFrameData()](VideoDecoder.getFrameData.html)

获取下一帧的解码数据

### [#](#VideoDecoder-on-string-eventName-function-callback) [VideoDecoder.on(string eventName, function callback)](VideoDecoder.on.html)

注册监听录制事件的回调函数。当对应事件触发时，回调函数会被执行

### [#](#VideoDecoder-off-string-eventName-function-callback) [VideoDecoder.off(string eventName, function callback)](VideoDecoder.off.html)

取消监听录制事件。当对应事件触发时，该回调函数不再执行

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/dez7LZm57hIy "在开发者工具中预览效果")

## [#](#低版本异步接口兼容) 低版本异步接口兼容

对基础库 2.16.1 版本前的 videoDecoder，所有的接口都没有返回 Promise 对象，若需要兼容低版本，则可采用如下方式的写法：

```
// 启动 videoDecoder
await new Promise(resolve => {
  decoder.on('start', resolve)
  decoder.start({
    source: 'http://...',
    abortAudio: true, // 不需要音频
  })
})
```

Incorrect translation.