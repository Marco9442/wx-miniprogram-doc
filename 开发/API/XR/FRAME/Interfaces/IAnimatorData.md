[xr-frame](./../) / [Exports](./../modules.html) / IAnimatorData

# [#](#Interface-IAnimatorData) Interface: IAnimatorData

[Animator](./../classes/Animator.html)组件数据接口。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [autoPlay](./IAnimatorData.html#autoPlay)
- [clipMap](./IAnimatorData.html#clipMap)
- [keyframe](./IAnimatorData.html#keyframe)

## [#](#Properties-2) Properties

### [#](#autoPlay) autoPlay

• `Optional` **autoPlay**: [`IAnimatorAutoPlay`](./IAnimatorAutoPlay.html)

默认自动播放的参数，详见[IAnimatorAutoPlay](./IAnimatorAutoPlay.html)。
`xml`中为`dict`数据。

---

### [#](#clipMap) clipMap

• `Optional` **clipMap**: `Object`

默认的片段名字映射，由于一个动画可以有多个片段，所以能通过映射由`Animator`中播放的名字 -> 动画资源中片段的名字。
`xml`中为`dict`数据。

#### [#](#Index-signature) Index signature

▪ [key: `string`]: `string`

---

### [#](#keyframe) keyframe

• **keyframe**: [`Animation`](./../classes/Animation.html)<`any`, `any`>

默认的`Keyframe`动画资源。
`xml`中为资源id。

Incorrect translation.