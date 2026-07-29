# [#](#Slot) Slot

在某些场合，我们希望使用和小程序UI组件一致的`slot`能力来做一些灵活的封装，解决复用。`xr-frame`同样支持`slot`，但在具体的用法上用一些限制，下面就让我们通过一个例子教大家使用。

## [#](#定义包含slot的组件) 定义包含`slot`的组件

首先我们需要定义一个能插入`slot`的组件，这个传统小程序区别不大，但注意**组件配置的`renderer`一定要是`xr-frame`**：

```
<xr-scene bind:ready="handleReady">
  <xr-light type="ambient" color="1 1 1" intensity="1" />
  <xr-light type="directional" rotation="40 70 0" color="1 1 1" intensity="3" cast-shadow />

  <slot></slot>
  
  <xr-node node-id="target"></xr-node>
  <xr-camera node-id="camera" clear-color="0.4 0.8 0.6 1" position="0 0 4" target="target" />
</xr-scene>
```

## [#](#定义要插入slot的组件) 定义要插入`slot`的组件

接下来我们便可以定义要插入的组件，同样需要**指定`renderer`为`xr-frame`**，但注意因为是作为`slot`并且受到**一个页面只能存在一个`xr-scene`**的约束，所以我们**不能**将此组件的根节点定义为`xr-scene`：

```
<xr-node>
  <xr-mesh geometry="cube" scale="0.5 0.5 0.5" position="1 0 0" />
  <xr-mesh geometry="sphere" scale="0.5 0.5 0.5" position="-1 0 0" />
</xr-node>
```

这里我定义了两个`mesh`，准备将其插入到第一个组件定义的场景中。

## [#](#用一个xr组件使用二者) 用一个`xr`组件使用二者

这一步是和传统小程序差别最大的，我们不能直接在`page`中使用`slot`，而是需要再新建一个`xr-frame`组件将二者包装起来。

首先创建一个`xr-frame`组件，定义其`json`配置，这里一定要注意**组件的名字不能是`xr-`类型的，否则会走到原生组件**。这里命名`xrTest`为定义了`slot`的组件，`xrSlot`是要插入的组件：

```
{
  "component": true,
  "renderer": "xr-frame",
  "usingComponents": {
    "xrTest": "../../components/xr-test/index",
    "xrSlot": "../../components/xr-slot/index"
  }
}
```

然后在`xml`中使用它：

```
<xrTest>
    <xrSlot />
</xrTest>
```

当然，你也可以不将要插入到`slot`中的内容定义为组件而是直接写`xr-frame`原生组件，比如：

```
<xrTest>
    <xr-node>
      <xr-mesh geometry="cube" scale="0.5 0.5 0.5" position="1 0 0" />
      <xr-mesh geometry="sphere" scale="0.5 0.5 0.5" position="-1 0 0" />
    </xr-node>
</xrTest>
```

## [#](#在页面中使用这个xr组件) 在页面中使用这个`xr`组件

最后一步就是使用最顶层的这个组件了，正常引入使用即可（这里命名为`xr-test-slot`）：

```
<view>
  <xr-test-slot
    disable-scroll
    id="main-frame"
    width="{{renderWidth}}"
    height="{{renderHeight}}"
    style="width:{{width}}px;height:{{height}}px;"
  />
</view>
```

Incorrect translation.