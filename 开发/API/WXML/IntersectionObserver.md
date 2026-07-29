# [#](#IntersectionObserver) IntersectionObserver

> 相关文档: [获取界面上的节点信息](../../framework/view/selector.html)

IntersectionObserver 对象，用于推断某些节点是否可以被用户看见、有多大比例可以被用户看见。

## [#](#方法) 方法

### [#](#IntersectionObserver-IntersectionObserver-relativeTo-string-selector-Object-margins) [IntersectionObserver IntersectionObserver.relativeTo(string selector, Object margins)](IntersectionObserver.relativeTo.html)

使用选择器指定一个节点，作为参照区域之一。

### [#](#IntersectionObserver-IntersectionObserver-relativeToViewport-Object-margins) [IntersectionObserver IntersectionObserver.relativeToViewport(Object margins)](IntersectionObserver.relativeToViewport.html)

指定页面显示区域作为参照区域之一

### [#](#IntersectionObserver-observe-string-targetSelector-IntersectionObserver-observeCallback-callback) [IntersectionObserver.observe(string targetSelector, IntersectionObserver.observeCallback callback)](IntersectionObserver.observe.html)

指定目标节点并开始监听相交状态变化情况

### [#](#IntersectionObserver-disconnect) [IntersectionObserver.disconnect()](IntersectionObserver.disconnect.html)

停止监听。回调函数将不再触发

Incorrect translation.