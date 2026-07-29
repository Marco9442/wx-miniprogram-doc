[xr-frame](./../) / [Exports](./../modules.html) / IKeyframeAnimationData

# [#](#Interface-IKeyframeAnimationData) Interface: IKeyframeAnimationData

`Keyframe`动画数据的动画部分。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [animation](./IKeyframeAnimationData.html#animation)
- [keyframe](./IKeyframeAnimationData.html#keyframe)

## [#](#Properties-2) Properties

### [#](#animation) animation

• **animation**: `Object`

动画部分。

#### [#](#Index-signature) Index signature

▪ [name: `string`]: [`IKeyframeAnimationInfo`](./IKeyframeAnimationInfo.html)

---

### [#](#keyframe) keyframe

• **keyframe**: `Object`

关键帧定义部分，可以参考[basic-animation](https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/doc/basic-animation.json)。

`name`为关键帧名字。
`key`为`0~100`的进度。
`prop`为属性序列，其规则为`[componentName].[prop1].[prop2].[prop3]...`，但是有一些特殊的缩写：
`position`、`scale`、`rotation`是`transform`组件下对应的属性，`material.u_xxx`则是设置材质的uniform。
`prop`的值，可以是数字或者数字数组。

#### [#](#Index-signature-2) Index signature

▪ [name: `string`]: { `[key: string]`: { `[prop: string]`: `number` | `number`[]; }; }

Incorrect translation.