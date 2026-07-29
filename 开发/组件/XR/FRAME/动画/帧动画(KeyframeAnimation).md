# [#](#帧动画) 帧动画

帧动画是一种内置的动画实现，提供给开发者类似于css动画的能力，去控制一个元素下所有组件的数据。

我们提供了一种资源来定义帧动画，之后可以用对应的加载器加载，在组件中使用。

## [#](#帧动画资源) 帧动画资源

首先我们要准备一个帧动画资源，它是被存储为`json`格式，大致如下：

```
{
  "keyframe": {
    "parent": {
      "0": {
        "rotation": [0, 0, 0],
      },
      "100": {
        "rotation": [0, 6.28, 0]
      }
    },
    "child": {
      "0": {
        "position.y": -0.5,
        "material.u_baseColorFactor": [0.48, 0.78, 0.64, 1]
      },
      "100": {
        "position.y": 1.5,
        "material.u_baseColorFactor": [0.176, 0.368, 0.937, 1]
      }
    }
  },
  "animation": {
    "parent": {
      "keyframe": "parent",
      "duration": 8,
      "ease": "linear",
      "loop": -1
    },
    "child": {
      "keyframe": "child",
      "duration": 4,
      "ease": "ease-in-out",
      "direction": "both",
      "loop": -1
    }
  }
}
```

可以看到其中有两个部分：`keyframe`和`animation`。

`keyframe`中定义了帧动画具体的行为，本质上类似于`css3`中的`keyframes`，其中进度的范围是`0~100`，每个进度下是动画具体影响的键和值。其中键的规则是`[组件].[属性].[属性2].[属性...]`，比如`transform.postion.x`，就是对应于使用了这个帧动画的元素下的`transform`组件的`position`属性的`x`属性变化。

当然我们不难看到，如果仅仅是按照这样的规则，一来是开发者必须要实现对应组件下每个属性的访问器，其次是对于一些常见的属性写起来会繁琐，再者对于材质动画会无从下手。为了解决这个问题，我做了一些实现上的优化：

1. 如果整个属性路径最终是`[组件].[属性]`的形式，则不需要写访问器，会自动设置。
2. `position`、`rotation`、`scale`会被自动代理到`transform`组件下。
3. `material`是一种特殊的定义，会被自动代理到`mesh`组件的材质的`uniform`下。

> 要注意，属性的值仅仅支持`number`、`number-array`和`color`类型的数据。
> 有了`keyframe`，再者就是`animation`了。`animation`中定义了真的暴露给`animator`的片段，其中第一级的每个键都是片段的名字，它对应的值就是其作为动画播放时的一些参数。`keyframe`定义这个片段对应于上面定义的哪个`keyframe`，`duration`是以秒为单位的时长，`loop`是默认循环次数（-1为永远循环），`delay`是播放延迟，`direction`是播放方向，默认`forwards`，可选`backwards`和`both`（在循环时交替前向反向），`ease`则是时间函数，决定动画的插值曲线。

> 支持的时间函数可见API文档：[noneParamsEaseFuncs](/miniprogram/dev/api/xr-frame/modules.html#noneParamsEaseFuncs)和[useParamsEaseFuncs](/miniprogram/dev/api/xr-frame/modules.html#noneParamsEaseFuncs)。

## [#](#使用) 使用

有了资源我们便可以加载使用它，和其他资源一样，`keyframe`资源遵循标准加载流程：

```
<xr-asset-load type="keyframe" asset-id="anim" src="/assets/keyframes/test.json" />
```

然后便可以引用使用：

```
<xr-node anim-keyframe="anim" anim-autoplay="clip:parent">
  <xr-node position="0 -0.5 3" anim-keyframe="anim" anim-autoplay="clip:child">
  </xr-node>
</xr-node>
```

注意这里使用了`anim-keyframe`字段来指定`animator`组件要默认使用哪个`keyframe`动画。

Incorrect translation.