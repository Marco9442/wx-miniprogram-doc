[xr-frame](./../) / [Exports](./../modules.html) / ARTracker

# [#](#Class-ARTracker) Class: ARTracker

AR追踪组件，配合[ARSystem](./ARSystem.html)和[Camera](./Camera.html)的`isARCamera`属性一起使用。
一般被代理到[XRARTracker](./XRARTracker.html)元素。

其提供了追踪的能力，节点将会自动同步识别到的追踪目标的位置和旋转，

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IARTrackerData`](./../interfaces/IARTrackerData.html)>

  ↳ **`ARTracker`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./ARTracker.html#constructor)

### [#](#Events) Events

- [onAdd](./ARTracker.html#onAdd)
- [onRelease](./ARTracker.html#onRelease)
- [onRemove](./ARTracker.html#onRemove)
- [onTick](./ARTracker.html#onTick)
- [onUpdate](./ARTracker.html#onUpdate)

### [#](#Properties) Properties

- [priority](./ARTracker.html#priority)
- [schema](./ARTracker.html#schema)
- [EVENTS](./ARTracker.html#EVENTS)

### [#](#Accessors) Accessors

- [arActive](./ARTracker.html#arActive)
- [el](./ARTracker.html#el)
- [errorMessage](./ARTracker.html#errorMessage)
- [gesture](./ARTracker.html#gesture)
- [mode](./ARTracker.html#mode)
- [scene](./ARTracker.html#scene)
- [score](./ARTracker.html#score)
- [state](./ARTracker.html#state)
- [version](./ARTracker.html#version)

### [#](#Methods) Methods

- [getData](./ARTracker.html#getData)
- [getPosition](./ARTracker.html#getPosition)
- [setData](./ARTracker.html#setData)
- [setDataOne](./ARTracker.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new ARTracker**()

#### [#](#Inherited-from) Inherited from

[Component](./Component.html).[constructor](./Component.html#constructor)

## [#](#Events-2) Events

### [#](#onAdd) onAdd

▸ **onAdd**(`parent`, `data`): `void`

所挂载的`element`被挂载到场景时触发的回调。

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `parent` | [`Element`](./Element.html) |
| `data` | [`IARTrackerData`](./../interfaces/IARTrackerData.html) |

#### [#](#Returns) Returns

`void`

#### [#](#Inherited-from-2) Inherited from

[Component](./Component.html).[onAdd](./Component.html#onAdd)

---

### [#](#onRelease) onRelease

▸ **onRelease**(`data`): `void`

从被挂载的`element`上被移除，或是`element`被销毁时，触发的回调。
一般用于释放持有的资源。

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IARTrackerData`](./../interfaces/IARTrackerData.html) |

#### [#](#Returns-2) Returns

`void`

#### [#](#Inherited-from-3) Inherited from

[Component](./Component.html).[onRelease](./Component.html#onRelease)

---

### [#](#onRemove) onRemove

▸ **onRemove**(`parent`, `data`): `void`

所挂载的`element`从父节点`parent`被移除时，或者自己从`element`上被移除时，触发的回调。
一般用于消除功能的运作。
**如果一个组件的元素直接被销毁了，那这个组件就不会经历onRemove而是直接进入onRelease。**

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `parent` | [`Element`](./Element.html) |
| `data` | [`IARTrackerData`](./../interfaces/IARTrackerData.html) |

#### [#](#Returns-3) Returns

`void`

#### [#](#Inherited-from-4) Inherited from

[Component](./Component.html).[onRemove](./Component.html#onRemove)

---

### [#](#onTick) onTick

▸ **onTick**(`deltaTime`, `data`): `void`

渲染每帧触发的回调。

#### [#](#Parameters-4) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `deltaTime` | `number` | 单位为毫秒(ms)。 |
| `data` | [`IARTrackerData`](./../interfaces/IARTrackerData.html) | - |

#### [#](#Returns-4) Returns

`void`

#### [#](#Inherited-from-5) Inherited from

[Component](./Component.html).[onTick](./Component.html#onTick)

---

### [#](#onUpdate) onUpdate

▸ **onUpdate**(`data`, `preData`): `void`

数据更新时触发的回调。

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IARTrackerData`](./../interfaces/IARTrackerData.html) |
| `preData` | [`IARTrackerData`](./../interfaces/IARTrackerData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number`

自定义组件的更新优先级。

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[priority](./Component.html#priority)

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html)

详见[ARTrackSchema](./../modules.html#ARTrackSchema)。

#### [#](#Overrides) Overrides

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[]

#### [#](#Overrides-2) Overrides

[Component](./Component.html).[EVENTS](./Component.html#EVENTS)

## [#](#Accessors-2) Accessors

### [#](#arActive) arActive

• `get` **arActive**(): `boolean`

是否已经检测到了目标。

#### [#](#Returns-6) Returns

`boolean`

---

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-7) Returns

[`Element`](./Element.html)

---

### [#](#errorMessage) errorMessage

• `get` **errorMessage**(): `string`

如果为错误状态，错误信息。

**`version`** v2.29.1

#### [#](#Returns-8) Returns

`string`

---

### [#](#gesture) gesture

• `get` **gesture**(): `number`

在`Hand`模式下，手势分类，正常`0~18`，无效为`-1`。

#### [#](#Returns-9) Returns

`number`

---

### [#](#mode) mode

• `get` **mode**(): [`TTrackMode`](./../modules.html#TTrackMode)

跟踪模式。

#### [#](#Returns-10) Returns

[`TTrackMode`](./../modules.html#TTrackMode)

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-11) Returns

[`Scene`](./Scene.html)

---

### [#](#score) score

• `get` **score**(): `number`

`Body`/`Hand`模式下，获取当前的置信度。
一般为`0~1`。

#### [#](#Returns-12) Returns

`number`

---

### [#](#state) state

• `get` **state**(): [`EARTrackerState`](./../enums/EARTrackerState.html)

当前识别状态。

**`version`** v2.29.1

#### [#](#Returns-13) Returns

[`EARTrackerState`](./../enums/EARTrackerState.html)

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-14) Returns

`number`

## [#](#Methods-2) Methods

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IARTrackerData`](./../interfaces/IARTrackerData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IARTrackerData`](./../interfaces/IARTrackerData.html) |

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-15) Returns

[`IARTrackerData`](./../interfaces/IARTrackerData.html)[`T`]

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#getPosition) getPosition

▸ **getPosition**(`point`, `output?`, `relativeToTracker?`): [`Vector3`](./Vector3.html)

在`Face`/`Body`/`Hand`模式下，获取某个特征点的位置。

#### [#](#Parameters-7) Parameters

| Name | Type | Default value | Description |
| --- | --- | --- | --- |
| `point` | `number` | `undefined` | 特征点索引，需要在`0~105`，否则返回`undefined`。 |
| `output?` | [`Vector3`](./Vector3.html) | `undefined` | - |
| `relativeToTracker` | `boolean` | `true` | 仅在`ar-system`的`pose3d`属性为`false`时生效。是否相对于`ARTracker`本身，默认为`true`，否则返回世界空间坐标。 |

#### [#](#Returns-16) Returns

[`Vector3`](./Vector3.html)

只有在`arActive`时才有值，否则返回`undefined`。

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IARTrackerData`](./../interfaces/IARTrackerData.html)> |

#### [#](#Returns-17) Returns

`void`

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[setData](./Component.html#setData)

---

### [#](#setDataOne) setDataOne

▸ **setDataOne**<`T`>(`key`, `value`): `void`

设置一个数据。

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IARTrackerData`](./../interfaces/IARTrackerData.html) |

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IARTrackerData`](./../interfaces/IARTrackerData.html)[`T`] |

#### [#](#Returns-18) Returns

`void`

#### [#](#Inherited-from-10) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.