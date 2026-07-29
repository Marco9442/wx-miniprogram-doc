[xr-frame](./../) / [Exports](./../modules.html) / Light

# [#](#Class-Light) Class: Light

灯光组件，一般被代理到[XRLight](./XRLight.html)元素。

注意整个场景只能存在一个`ambient`光源，第一个`directional`光源将会成为主光源，也只有这个光源能够产生阴影。
目前最多支持四个追加光源。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`ILightData`](./../interfaces/ILightData.html)>

  ↳ **`Light`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Light.html#constructor)

### [#](#Events) Events

- [onAdd](./Light.html#onAdd)
- [onRelease](./Light.html#onRelease)
- [onRemove](./Light.html#onRemove)
- [onTick](./Light.html#onTick)
- [onUpdate](./Light.html#onUpdate)

### [#](#Properties) Properties

- [priority](./Light.html#priority)
- [schema](./Light.html#schema)
- [EVENTS](./Light.html#EVENTS)

### [#](#Accessors) Accessors

- [castShadow](./Light.html#castShadow)
- [color](./Light.html#color)
- [el](./Light.html#el)
- [innerConeAngle](./Light.html#innerConeAngle)
- [intensity](./Light.html#intensity)
- [outerConeAngle](./Light.html#outerConeAngle)
- [range](./Light.html#range)
- [scene](./Light.html#scene)
- [shadowBias](./Light.html#shadowBias)
- [shadowDistance](./Light.html#shadowDistance)
- [type](./Light.html#type)
- [version](./Light.html#version)

### [#](#Methods) Methods

- [getData](./Light.html#getData)
- [setData](./Light.html#setData)
- [setDataOne](./Light.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Light**()

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
| `data` | [`ILightData`](./../interfaces/ILightData.html) |

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
| `data` | [`ILightData`](./../interfaces/ILightData.html) |

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
| `data` | [`ILightData`](./../interfaces/ILightData.html) |

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
| `data` | [`ILightData`](./../interfaces/ILightData.html) |

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
| `data` | [`ILightData`](./../interfaces/ILightData.html) |
| `preData` | [`ILightData`](./../interfaces/ILightData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number` = `200`

自定义组件的更新优先级。

#### [#](#Overrides) Overrides

[Component](./Component.html).[priority](./Component.html#priority)

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html)

详见[LightSchema](./../modules.html#LightSchema)。

#### [#](#Overrides-2) Overrides

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[] = `[]`

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[EVENTS](./Component.html#EVENTS)

## [#](#Accessors-2) Accessors

### [#](#castShadow) castShadow

• `get` **castShadow**(): `boolean`

#### [#](#Returns-6) Returns

`boolean`

---

### [#](#color) color

• `get` **color**(): `number`[]

#### [#](#Returns-7) Returns

`number`[]

---

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-8) Returns

[`Element`](./Element.html)

---

### [#](#innerConeAngle) innerConeAngle

• `get` **innerConeAngle**(): `number`

#### [#](#Returns-9) Returns

`number`

---

### [#](#intensity) intensity

• `get` **intensity**(): `number`

#### [#](#Returns-10) Returns

`number`

---

### [#](#outerConeAngle) outerConeAngle

• `get` **outerConeAngle**(): `number`

#### [#](#Returns-11) Returns

`number`

---

### [#](#range) range

• `get` **range**(): `number`

#### [#](#Returns-12) Returns

`number`

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-13) Returns

[`Scene`](./Scene.html)

---

### [#](#shadowBias) shadowBias

• `get` **shadowBias**(): `number`

#### [#](#Returns-14) Returns

`number`

---

### [#](#shadowDistance) shadowDistance

• `get` **shadowDistance**(): `number`

#### [#](#Returns-15) Returns

`number`

---

### [#](#type) type

• `get` **type**(): `ELightType`

#### [#](#Returns-16) Returns

`ELightType`

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-17) Returns

`number`

## [#](#Methods-2) Methods

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`ILightData`](./../interfaces/ILightData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`ILightData`](./../interfaces/ILightData.html) |

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-18) Returns

[`ILightData`](./../interfaces/ILightData.html)[`T`]

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`ILightData`](./../interfaces/ILightData.html)> |

#### [#](#Returns-19) Returns

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
| `T` | extends keyof [`ILightData`](./../interfaces/ILightData.html) |

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`ILightData`](./../interfaces/ILightData.html)[`T`] |

#### [#](#Returns-20) Returns

`void`

#### [#](#Inherited-from-10) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.