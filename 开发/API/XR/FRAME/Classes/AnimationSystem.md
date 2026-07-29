[xr-frame](./../) / [Exports](./../modules.html) / AnimationSystem

# [#](#Class-AnimationSystem) Class: AnimationSystem

动画系统，负责整个场景动画的管理。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IAnimationSystemData`](./../interfaces/IAnimationSystemData.html)>

  ↳ **`AnimationSystem`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./AnimationSystem.html#constructor)

### [#](#Events) Events

- [onAdd](./AnimationSystem.html#onAdd)
- [onRelease](./AnimationSystem.html#onRelease)
- [onRemove](./AnimationSystem.html#onRemove)
- [onTick](./AnimationSystem.html#onTick)
- [onUpdate](./AnimationSystem.html#onUpdate)

### [#](#Properties) Properties

- [priority](./AnimationSystem.html#priority)
- [schema](./AnimationSystem.html#schema)
- [EVENTS](./AnimationSystem.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./AnimationSystem.html#el)
- [scene](./AnimationSystem.html#scene)
- [version](./AnimationSystem.html#version)

### [#](#Methods) Methods

- [getData](./AnimationSystem.html#getData)
- [setData](./AnimationSystem.html#setData)
- [setDataOne](./AnimationSystem.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new AnimationSystem**()

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
| `data` | [`IAnimationSystemData`](./../interfaces/IAnimationSystemData.html) |

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
| `data` | [`IAnimationSystemData`](./../interfaces/IAnimationSystemData.html) |

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
| `data` | [`IAnimationSystemData`](./../interfaces/IAnimationSystemData.html) |

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
| `data` | [`IAnimationSystemData`](./../interfaces/IAnimationSystemData.html) |

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
| `data` | [`IAnimationSystemData`](./../interfaces/IAnimationSystemData.html) |
| `preData` | [`IAnimationSystemData`](./../interfaces/IAnimationSystemData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number` = `100`

自定义组件的更新优先级。

#### [#](#Overrides) Overrides

[Component](./Component.html).[priority](./Component.html#priority)

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html) = `{}`

自定义组件的`schema`。

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[] = `[]`

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[EVENTS](./Component.html#EVENTS)

## [#](#Accessors-2) Accessors

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-6) Returns

[`Element`](./Element.html)

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-7) Returns

[`Scene`](./Scene.html)

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-8) Returns

`number`

## [#](#Methods-2) Methods

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IAnimationSystemData`](./../interfaces/IAnimationSystemData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends `never` |

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-9) Returns

[`IAnimationSystemData`](./../interfaces/IAnimationSystemData.html)[`T`]

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IAnimationSystemData`](./../interfaces/IAnimationSystemData.html)> |

#### [#](#Returns-10) Returns

`void`

#### [#](#Inherited-from-10) Inherited from

[Component](./Component.html).[setData](./Component.html#setData)

---

### [#](#setDataOne) setDataOne

▸ **setDataOne**<`T`>(`key`, `value`): `void`

设置一个数据。

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends `never` |

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IAnimationSystemData`](./../interfaces/IAnimationSystemData.html)[`T`] |

#### [#](#Returns-11) Returns

`void`

#### [#](#Inherited-from-11) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.