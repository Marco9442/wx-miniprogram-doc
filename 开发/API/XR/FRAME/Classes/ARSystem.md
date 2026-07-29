[xr-frame](./../) / [Exports](./../modules.html) / ARSystem

# [#](#Class-ARSystem) Class: ARSystem

AR系统，负责整个场景AR相关对象的管理。

代理自小程序的`VKSession`。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IARSystemData`](./../interfaces/IARSystemData.html)>

  ↳ **`ARSystem`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./ARSystem.html#constructor)

### [#](#Events) Events

- [onAdd](./ARSystem.html#onAdd)
- [onRelease](./ARSystem.html#onRelease)
- [onRemove](./ARSystem.html#onRemove)
- [onTick](./ARSystem.html#onTick)
- [onUpdate](./ARSystem.html#onUpdate)

### [#](#Properties) Properties

- [priority](./ARSystem.html#priority)
- [schema](./ARSystem.html#schema)
- [EVENTS](./ARSystem.html#EVENTS)

### [#](#Accessors) Accessors

- [arModes](./ARSystem.html#arModes)
- [arVersion](./ARSystem.html#arVersion)
- [el](./ARSystem.html#el)
- [posCount](./ARSystem.html#posCount)
- [ready](./ARSystem.html#ready)
- [scene](./ARSystem.html#scene)
- [supported](./ARSystem.html#supported)
- [version](./ARSystem.html#version)

### [#](#Methods) Methods

- [forceSetViewMatrix](./ARSystem.html#forceSetViewMatrix)
- [getARRawData](./ARSystem.html#getARRawData)
- [getData](./ARSystem.html#getData)
- [placeHere](./ARSystem.html#placeHere)
- [resetPlane](./ARSystem.html#resetPlane)
- [setData](./ARSystem.html#setData)
- [setDataOne](./ARSystem.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new ARSystem**()

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
| `data` | [`IARSystemData`](./../interfaces/IARSystemData.html) |

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
| `data` | [`IARSystemData`](./../interfaces/IARSystemData.html) |

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
| `data` | [`IARSystemData`](./../interfaces/IARSystemData.html) |

#### [#](#Returns-3) Returns

`void`

#### [#](#Inherited-from-4) Inherited from

[Component](./Component.html).[onRemove](./Component.html#onRemove)

---

### [#](#onTick) onTick

▸ **onTick**(`deltaTime`, `data`): `void`

渲染每帧触发的回调。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `deltaTime` | `number` |
| `data` | [`IARSystemData`](./../interfaces/IARSystemData.html) |

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
| `data` | [`IARSystemData`](./../interfaces/IARSystemData.html) |
| `preData` | [`IARSystemData`](./../interfaces/IARSystemData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number` = `110`

自定义组件的更新优先级。

#### [#](#Overrides) Overrides

[Component](./Component.html).[priority](./Component.html#priority)

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html)

详见[ARSystemSchema](./../modules.html#ARSystemSchema)。

#### [#](#Overrides-2) Overrides

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[]

#### [#](#Overrides-3) Overrides

[Component](./Component.html).[EVENTS](./Component.html#EVENTS)

## [#](#Accessors-2) Accessors

### [#](#arModes) arModes

• `get` **arModes**(): [`TTrackMode`](./../modules.html#TTrackMode)[]

当前启动的追踪模式。

#### [#](#Returns-6) Returns

[`TTrackMode`](./../modules.html#TTrackMode)[]

---

### [#](#arVersion) arVersion

• `get` **arVersion**(): `number`

当前启动的AR系统版本。

#### [#](#Returns-7) Returns

`number`

---

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-8) Returns

[`Element`](./Element.html)

---

### [#](#posCount) posCount

• `get` **posCount**(): `number`

在`Face`/`Body`/`Hand`模式下，当前识别到的姿态数量。

#### [#](#Returns-9) Returns

`number`

---

### [#](#ready) ready

• `get` **ready**(): `boolean`

当前是否已经可用。

#### [#](#Returns-10) Returns

`boolean`

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-11) Returns

[`Scene`](./Scene.html)

---

### [#](#supported) supported

• `get` **supported**(): `boolean`

当前设备是否启动成功。

#### [#](#Returns-12) Returns

`boolean`

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-13) Returns

`number`

## [#](#Methods-2) Methods

### [#](#forceSetViewMatrix) forceSetViewMatrix

▸ **forceSetViewMatrix**(`camera`, `mat`): `void`

提供一个修改某个设置为`isARCamera`的相机的试图矩阵的手段。

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `camera` | [`Camera`](./Camera.html) |
| `mat` | [`Matrix4`](./Matrix4.html) |

#### [#](#Returns-14) Returns

`void`

---

### [#](#getARRawData) getARRawData

▸ **getARRawData**(): [`IARRawData`](./../interfaces/IARRawData.html)

获取AR的追踪的原始数据。

#### [#](#Returns-15) Returns

[`IARRawData`](./../interfaces/IARRawData.html)

---

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IARSystemData`](./../interfaces/IARSystemData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IARSystemData`](./../interfaces/IARSystemData.html) |

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-16) Returns

[`IARSystemData`](./../interfaces/IARSystemData.html)[`T`]

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#placeHere) placeHere

▸ **placeHere**(`nodeIdOrElement`, `switchVisible?`): `boolean`

在`Plane`模式下，同步某个节点到当前追踪到的和平面的交点。

#### [#](#Parameters-8) Parameters

| Name | Type | Default value | Description |
| --- | --- | --- | --- |
| `nodeIdOrElement` | `string` | [`Element`](./Element.html) | `undefined` | 节点的`nodeId`或是`element`引用。 |
| `switchVisible` | `boolean` | `true` | 是否要自动切换显示或隐藏。 |

#### [#](#Returns-17) Returns

`boolean`

是否放置成功

---

### [#](#resetPlane) resetPlane

▸ **resetPlane**(): `void`

在`Plane`模式下，重置平面。

#### [#](#Returns-18) Returns

`void`

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IARSystemData`](./../interfaces/IARSystemData.html)> |

#### [#](#Returns-19) Returns

`void`

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[setData](./Component.html#setData)

---

### [#](#setDataOne) setDataOne

▸ **setDataOne**<`T`>(`key`, `value`): `void`

设置一个数据。

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IARSystemData`](./../interfaces/IARSystemData.html) |

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IARSystemData`](./../interfaces/IARSystemData.html)[`T`] |

#### [#](#Returns-20) Returns

`void`

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.