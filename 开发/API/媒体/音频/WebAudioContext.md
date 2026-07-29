# [#](#WebAudioContext) WebAudioContext

> 基础库 2.19.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

WebAudioContext 实例，通过[wx.createWebAudioContext](wx.createWebAudioContext.html) 接口获取该实例。

## [#](#属性) 属性

### [#](#string-state) string state

当前WebAudio上下文的状态。可能的值如下：suspended（暂停）、running（正在运行）、closed（已关闭）。需要注意的是，不要在 audioContext close后再访问state属性

### [#](#function-onstatechange) function onstatechange

可写属性，开发者可以对该属性设置一个监听函数，当WebAudio状态改变的时候，会触发开发者设置的监听函数。

### [#](#number-currentTime) number currentTime

获取当前上下文的时间戳。

### [#](#WebAudioContextNode-destination) [WebAudioContextNode](WebAudioContextNode.html) destination

当前上下文的最终目标节点，一般是音频渲染设备。

### [#](#AudioListener-listener) [AudioListener](AudioListener.html) listener

空间音频监听器。

### [#](#number-sampleRate) number sampleRate

采样率，通常在8000-96000之间，通常44100hz的采样率最为常见。

## [#](#方法) 方法

### [#](#Promise-WebAudioContext-close) [Promise WebAudioContext.close()](WebAudioContext.close.html)

关闭WebAudioContext

### [#](#Promise-WebAudioContext-resume) [Promise WebAudioContext.resume()](WebAudioContext.resume.html)

同步恢复已经被暂停的WebAudioContext上下文

### [#](#Promise-WebAudioContext-suspend) [Promise WebAudioContext.suspend()](WebAudioContext.suspend.html)

同步暂停WebAudioContext上下文

### [#](#IIRFilterNode-WebAudioContext-createIIRFilter-Array-number-feedforward-Array-number-feedback) [IIRFilterNode WebAudioContext.createIIRFilter(Array.<number> feedforward, Array.<number> feedback)](WebAudioContext.createIIRFilter.html)

创建一个IIRFilterNode

### [#](#WaveShaperNode-WebAudioContext-createWaveShaper) [WaveShaperNode WebAudioContext.createWaveShaper()](WebAudioContext.createWaveShaper.html)

创建一个WaveShaperNode

### [#](#ConstantSourceNode-WebAudioContext-createConstantSource) [ConstantSourceNode WebAudioContext.createConstantSource()](WebAudioContext.createConstantSource.html)

创建一个ConstantSourceNode

### [#](#OscillatorNode-WebAudioContext-createOscillator) [OscillatorNode WebAudioContext.createOscillator()](WebAudioContext.createOscillator.html)

创建一个OscillatorNode

### [#](#GainNode-WebAudioContext-createGain) [GainNode WebAudioContext.createGain()](WebAudioContext.createGain.html)

创建一个GainNode

### [#](#PeriodicWaveNode-WebAudioContext-createPeriodicWave-Float32Array-real-Float32Array-imag-object-constraints) [PeriodicWaveNode WebAudioContext.createPeriodicWave(Float32Array real, Float32Array imag, object constraints)](WebAudioContext.createPeriodicWave.html)

创建一个PeriodicWaveNode

### [#](#BiquadFilterNode-WebAudioContext-createBiquadFilter) [BiquadFilterNode WebAudioContext.createBiquadFilter()](WebAudioContext.createBiquadFilter.html)

创建一个BiquadFilterNode

### [#](#BufferSourceNode-WebAudioContext-createBufferSource) [BufferSourceNode WebAudioContext.createBufferSource()](WebAudioContext.createBufferSource.html)

创建一个BufferSourceNode实例，通过AudioBuffer对象来播放音频数据。

### [#](#ChannelMergerNode-WebAudioContext-createChannelMerger-number-numberOfInputs) [ChannelMergerNode WebAudioContext.createChannelMerger(number numberOfInputs)](WebAudioContext.createChannelMerger.html)

创建一个ChannelMergerNode

### [#](#ChannelSplitterNode-WebAudioContext-createChannelSplitter-number-numberOfOutputs) [ChannelSplitterNode WebAudioContext.createChannelSplitter(number numberOfOutputs)](WebAudioContext.createChannelSplitter.html)

创建一个ChannelSplitterNode

### [#](#DelayNode-WebAudioContext-createDelay-number-maxDelayTime) [DelayNode WebAudioContext.createDelay(number maxDelayTime)](WebAudioContext.createDelay.html)

创建一个DelayNode

### [#](#DynamicsCompressorNode-WebAudioContext-createDynamicsCompressor) [DynamicsCompressorNode WebAudioContext.createDynamicsCompressor()](WebAudioContext.createDynamicsCompressor.html)

创建一个DynamicsCompressorNode

### [#](#ScriptProcessorNode-WebAudioContext-createScriptProcessor-number-bufferSize-number-numberOfInputChannels-number-numberOfOutputChannels) [ScriptProcessorNode WebAudioContext.createScriptProcessor(number bufferSize, number numberOfInputChannels, number numberOfOutputChannels)](WebAudioContext.createScriptProcessor.html)

创建一个ScriptProcessorNode

### [#](#AnalyserNode-WebAudioContext-createAnalyser) [AnalyserNode WebAudioContext.createAnalyser()](WebAudioContext.createAnalyser.html)

创建一个 AnalyserNode 。可以用来获取音频时间和频率数据，以及实现数据可视化。

### [#](#PannerNode-WebAudioContext-createPanner) [PannerNode WebAudioContext.createPanner()](WebAudioContext.createPanner.html)

创建一个PannerNode

### [#](#AudioBuffer-WebAudioContext-createBuffer-number-numOfChannels-number-length-number-sampleRate) [AudioBuffer WebAudioContext.createBuffer(number numOfChannels, number length, number sampleRate)](WebAudioContext.createBuffer.html)

创建一个AudioBuffer，代表着一段驻留在内存中的短音频

### [#](#AudioBuffer-WebAudioContext-decodeAudioData-ArrayBuffer-audioData-function-successCallback-function-errorCallback) [AudioBuffer WebAudioContext.decodeAudioData(ArrayBuffer audioData, function successCallback, function errorCallback)](WebAudioContext.decodeAudioData.html)

异步解码一段资源为AudioBuffer。

## [#](#示例代码) 示例代码

```
// 监听状态
const audioCtx = wx.createWebAudioContext()
audioCtx.onstatechange = () => {
  console.log(ctx.state)
}
setTimeout(audioCtx.suspend, 1000)
setTimeout(audioCtx.resume, 2000)
```

Incorrect translation.