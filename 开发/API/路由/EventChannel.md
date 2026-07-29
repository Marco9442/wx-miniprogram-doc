# [#](#EventChannel) EventChannel

> 基础库 2.7.3 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

页面间事件通信通道

## [#](#方法) 方法

### [#](#EventChannel-emit-string-eventName-any-args) [EventChannel.emit(string eventName, any args)](EventChannel.emit.html)

触发一个事件

### [#](#EventChannel-on-string-eventName-EventCallback-fn) [EventChannel.on(string eventName, EventCallback fn)](EventChannel.on.html)

持续监听一个事件

### [#](#EventChannel-once-string-eventName-EventCallback-fn) [EventChannel.once(string eventName, EventCallback fn)](EventChannel.once.html)

监听一个事件一次，触发后失效

### [#](#EventChannel-off-string-eventName-EventCallback-fn) [EventChannel.off(string eventName, EventCallback fn)](EventChannel.off.html)

取消监听一个事件。给出第二个参数时，只取消给出的监听函数，否则取消所有监听函数

Incorrect translation.