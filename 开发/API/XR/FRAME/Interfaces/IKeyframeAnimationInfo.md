[xr-frame](./../) / [Exports](./../modules.html) / IKeyframeAnimationInfo

# [#](#Interface-IKeyframeAnimationInfo) Interface: IKeyframeAnimationInfo

`Keyframe`动画数据的动画部分。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [delay](./IKeyframeAnimationInfo.html#delay)
- [direction](./IKeyframeAnimationInfo.html#direction)
- [duration](./IKeyframeAnimationInfo.html#duration)
- [ease](./IKeyframeAnimationInfo.html#ease)
- [easeParams](./IKeyframeAnimationInfo.html#easeParams)
- [keyframe](./IKeyframeAnimationInfo.html#keyframe)
- [loop](./IKeyframeAnimationInfo.html#loop)

## [#](#Properties-2) Properties

### [#](#delay) delay

• `Optional` **delay**: `number`

播放延迟。

---

### [#](#direction) direction

• `Optional` **direction**: [`TDirection`](./../modules.html#TDirection)

播放方向。

---

### [#](#duration) duration

• **duration**: `number`

动画长度(s)。

---

### [#](#ease) ease

• **ease**: `string`

动画插值方式，详见[noneParamsEaseFuncs](./../modules.html#noneParamsEaseFuncs)和[useParamsEaseFuncs](./../modules.html#useParamsEaseFuncs)。

---

### [#](#easeParams) easeParams

• `Optional` **easeParams**: `number`[]

如果是可以接受参数的插值方式，指定参数。

---

### [#](#keyframe) keyframe

• **keyframe**: `string`

指定动画使用的Keyframe。

---

### [#](#loop) loop

• `Optional` **loop**: `number`

循环次数，`0`为不循环，`-1`为永远循环。

Incorrect translation.