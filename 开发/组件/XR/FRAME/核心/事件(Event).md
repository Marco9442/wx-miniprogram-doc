# [#](#事件) 事件

事件管理器从属于元素，提供给组件的设计者一个向使用者派发事件的手段。

事件有两种使用方式，一种是走传统的脚本逻辑，一种是用小程序在`wxml`中的事件绑定。

## [#](#脚本逻辑) 脚本逻辑

在脚本中使用事件很简单，用一段代码例子来解释：

```
// 定义监听器，比如这个事件的参数类型是`number`
function handleTest(params: number, sender: XrFrame.Element) {
  console.log('test', params, sender);
}

// 添加事件监听器
el.event.add('test', handleTest);

// 移除事件监听器
el.event.remove('test', handleTest);

// 添加事件监听器，但会在一次触发后自动移除
el.event.addOnce('test', handleTest);
```

## [#](#wxml绑定) wxml绑定

在`wxml`中进行事件绑定会稍微复杂一些，还是来看个例子：

```
<xr-scene bind:tick="handleTick">
</xr-scene>
```

这里我们给`xr-scene`标签绑定了`tick`事件，事件的`handler`被定义在组件的`method`内，和其他的小程序组件一致。

这里要注意的是如此绑定的事件获取事件参数的方法不同：

```
handleTick: function(event) {
  const {value, el} = event.detail;
}
```

这里取出的`value`就是事件的参数，`el`则是派发事件的那个元素。

## [#](#派发事件) 派发事件

知道了如何监听事件，我们还需要知道如何派发，依照以上两种监听方式，事件的触发有不同参数：

```
el.event.trigger(type, event, immediately, toXML, bubbles);
```

`immediately`是指是否要立即触发，默认是`true`，如果为`false`，则会对当帧同名的事件进行合并，然后在**当帧组件生命周期的驱动前**派发。

`toXML`是说这个事件是否要派发到`xml`上，来允许开发者使用事件绑定，默认是`true`。

`bubbles`是指事件是否要沿着`xr-frame`的节点树冒泡，同时也会影响在`xml`中的冒泡。

> 注意在[Shadow元素](./shadow.html)的子孙元素中，如果要让事件能够在`xml`中被绑定，`bubbles`必须为`true`。

Incorrect translation.