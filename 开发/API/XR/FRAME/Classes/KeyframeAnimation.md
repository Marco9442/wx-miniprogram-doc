[xr-frame](./../) / [Exports](./../modules.html) / KeyframeAnimation

# [#](#Class-KeyframeAnimation) Class: KeyframeAnimation

`Keyframe`动画。

## [#](#Hierarchy) Hierarchy

- [`Animation`](./Animation.html)<[`IKeyframeAnimationData`](./../interfaces/IKeyframeAnimationData.html), [`IKeyframeAnimationOptions`](./../interfaces/IKeyframeAnimationOptions.html)>

  ↳ **`KeyframeAnimation`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./KeyframeAnimation.html#constructor)

### [#](#Events) Events

- [onInit](./KeyframeAnimation.html#onInit)
- [onPause](./KeyframeAnimation.html#onPause)
- [onPlay](./KeyframeAnimation.html#onPlay)
- [onResume](./KeyframeAnimation.html#onResume)
- [onStop](./KeyframeAnimation.html#onStop)
- [onUpdate](./KeyframeAnimation.html#onUpdate)

### [#](#Properties) Properties

- [clipNames](./KeyframeAnimation.html#clipNames)

### [#](#Accessors) Accessors

- [scene](./KeyframeAnimation.html#scene)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new KeyframeAnimation**(`_scene`, `data`)

#### [#](#Parameters) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `_scene` | [`Scene`](./Scene.html) | 场景实例。 |
| `data` | [`IKeyframeAnimationData`](./../interfaces/IKeyframeAnimationData.html) | 初始化动画数据。 |

#### [#](#Inherited-from) Inherited from

[Animation](./Animation.html).[constructor](./Animation.html#constructor)

## [#](#Events-2) Events

### [#](#onInit) onInit

▸ **onInit**(`data`): `void`

动画初始化时执行的生命周期，只会执行一次。

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IKeyframeAnimationData`](./../interfaces/IKeyframeAnimationData.html) |

#### [#](#Returns) Returns

`void`

#### [#](#Inherited-from-2) Inherited from

[Animation](./Animation.html).[onInit](./Animation.html#onInit)

---

### [#](#onPause) onPause

▸ **onPause**(`el`): `void`

在动画暂停时执行的回调。

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `el` | [`Element`](./Element.html) |

#### [#](#Returns-2) Returns

`void`

#### [#](#Inherited-from-3) Inherited from

[Animation](./Animation.html).[onPause](./Animation.html#onPause)

---

### [#](#onPlay) onPlay

▸ **onPlay**(`el`, `clipName`, `options`): [`IKeyframeAnimationInfo`](./../interfaces/IKeyframeAnimationInfo.html)

动画开始播放时执行的生命周期。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `el` | [`Element`](./Element.html) |
| `clipName` | `string` |
| `options` | [`IKeyframeAnimationOptions`](./../interfaces/IKeyframeAnimationOptions.html) |

#### [#](#Returns-3) Returns

[`IKeyframeAnimationInfo`](./../interfaces/IKeyframeAnimationInfo.html)

返回本次播放片段的参数，必须包括时长`duration`(s)，可选循环次数`loop`、延迟`delay`和方向`direction`。

#### [#](#Inherited-from-4) Inherited from

[Animation](./Animation.html).[onPlay](./Animation.html#onPlay)

---

### [#](#onResume) onResume

▸ **onResume**(`el`): `void`

在动画从暂停状态唤醒时执行的回调。

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `el` | [`Element`](./Element.html) |

#### [#](#Returns-4) Returns

`void`

#### [#](#Inherited-from-5) Inherited from

[Animation](./Animation.html).[onResume](./Animation.html#onResume)

---

### [#](#onStop) onStop

▸ **onStop**(`el`): `void`

在动画停止时执行的回调。

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `el` | [`Element`](./Element.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Animation](./Animation.html).[onStop](./Animation.html#onStop)

---

### [#](#onUpdate) onUpdate

▸ **onUpdate**(`el`, `progress`, `reverse`): `void`

在动画更新时执行的回调。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `el` | [`Element`](./Element.html) |
| `progress` | `number` |
| `reverse` | `boolean` |

#### [#](#Returns-6) Returns

`void`

#### [#](#Inherited-from-7) Inherited from

[Animation](./Animation.html).[onUpdate](./Animation.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#clipNames) clipNames

• **clipNames**: `string`[]

动画所有的片段名字，必须在`onInit`中被初始化。

#### [#](#Inherited-from-8) Inherited from

[Animation](./Animation.html).[clipNames](./Animation.html#clipNames)

## [#](#Accessors-2) Accessors

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

场景实例。

#### [#](#Returns-7) Returns

[`Scene`](./Scene.html)

Incorrect translation.