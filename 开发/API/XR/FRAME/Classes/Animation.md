[xr-frame](./../) / [Exports](./../modules.html) / Animation

# [#](#Class-Animation-IData-IOptions) Class: Animation<IData, IOptions>

动画资源基类，被[Animator](./Animator.html)使用，可以继承它来实现具体的动画。

## [#](#Type-parameters) Type parameters

| Name | Type | Description |
| --- | --- | --- |
| `IData` | `any` | 动画初始化接受的数据。 |
| `IOptions` | `any` | 动画播放时接受的额外追加选项。 |

## [#](#Hierarchy) Hierarchy

- **`Animation`**

  ↳ [`KeyframeAnimation`](./KeyframeAnimation.html)

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Animation.html#constructor)

### [#](#Events) Events

- [onInit](./Animation.html#onInit)
- [onPause](./Animation.html#onPause)
- [onPlay](./Animation.html#onPlay)
- [onResume](./Animation.html#onResume)
- [onStop](./Animation.html#onStop)
- [onUpdate](./Animation.html#onUpdate)

### [#](#Properties) Properties

- [clipNames](./Animation.html#clipNames)

### [#](#Accessors) Accessors

- [scene](./Animation.html#scene)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Animation**<`IData`, `IOptions`>(`_scene`, `data`)

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `IData` | `any` |
| `IOptions` | `any` |

#### [#](#Parameters) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `_scene` | [`Scene`](./Scene.html) | 场景实例。 |
| `data` | `IData` | 初始化动画数据。 |

## [#](#Events-2) Events

### [#](#onInit) onInit

▸ **onInit**(`data`): `void`

动画初始化时执行的生命周期，只会执行一次。

#### [#](#Parameters-2) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `data` | `IData` | 初始化动画数据。 |

#### [#](#Returns) Returns

`void`

---

### [#](#onPause) onPause

▸ **onPause**(`el`): `void`

在动画暂停时执行的回调。

#### [#](#Parameters-3) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `el` | [`Element`](./Element.html) | 本次播放作用于的`element`。 |

#### [#](#Returns-2) Returns

`void`

---

### [#](#onPlay) onPlay

▸ **onPlay**(`el`, `clipName`, `options`): `Object`

动画开始播放时执行的生命周期。

#### [#](#Parameters-4) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `el` | [`Element`](./Element.html) | 本次播放作用于的`element`，一个动画可能作用于多个`element`，可以在这里区分。 |
| `clipName` | `string` | 本次播放的片段名字。 |
| `options` | `IOptions` | 本次播放时的附加选项。 |

#### [#](#Returns-3) Returns

`Object`

返回本次播放片段的参数，必须包括时长`duration`(s)，可选循环次数`loop`、延迟`delay`和方向`direction`。

| Name | Type |
| --- | --- |
| `delay?` | `number` |
| `direction?` | [`TDirection`](./../modules.html#TDirection) |
| `duration` | `number` |
| `loop?` | `number` |

---

### [#](#onResume) onResume

▸ **onResume**(`el`): `void`

在动画从暂停状态唤醒时执行的回调。

#### [#](#Parameters-5) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `el` | [`Element`](./Element.html) | 本次播放作用于的`element`。 |

#### [#](#Returns-4) Returns

`void`

---

### [#](#onStop) onStop

▸ **onStop**(`el`): `void`

在动画停止时执行的回调。

#### [#](#Parameters-6) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `el` | [`Element`](./Element.html) | 本次播放作用于的`element`。 |

#### [#](#Returns-5) Returns

`void`

---

### [#](#onUpdate) onUpdate

▸ **onUpdate**(`el`, `progress`, `reverse`): `void`

在动画更新时执行的回调。

#### [#](#Parameters-7) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `el` | [`Element`](./Element.html) | 本次播放作用于的`element`。 |
| `progress` | `number` | 播放进度，范围为线性的`0~1`。 |
| `reverse` | `boolean` | 本次播放是否反向。 |

#### [#](#Returns-6) Returns

`void`

## [#](#Properties-2) Properties

### [#](#clipNames) clipNames

• **clipNames**: `string`[]

动画所有的片段名字，必须在`onInit`中被初始化。

## [#](#Accessors-2) Accessors

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

场景实例。

#### [#](#Returns-7) Returns

[`Scene`](./Scene.html)

Incorrect translation.