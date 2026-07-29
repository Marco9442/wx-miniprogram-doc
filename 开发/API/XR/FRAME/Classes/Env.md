[xr-frame](./../) / [Exports](./../modules.html) / Env

# [#](#Class-Env) Class: Env

一般被代理到[XRARTracker](./XRARTracker.html)元素。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IEnvData`](./../interfaces/IEnvData.html)>

  ↳ **`Env`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Env.html#constructor)

### [#](#Events) Events

- [onAdd](./Env.html#onAdd)
- [onRelease](./Env.html#onRelease)
- [onRemove](./Env.html#onRemove)
- [onTick](./Env.html#onTick)
- [onUpdate](./Env.html#onUpdate)

### [#](#Properties) Properties

- [priority](./Env.html#priority)
- [schema](./Env.html#schema)
- [EVENTS](./Env.html#EVENTS)

### [#](#Accessors) Accessors

- [diffuseExp](./Env.html#diffuseExp)
- [diffuseSH](./Env.html#diffuseSH)
- [el](./Env.html#el)
- [hasDiffuse](./Env.html#hasDiffuse)
- [hasSpecular](./Env.html#hasSpecular)
- [isSky2D](./Env.html#isSky2D)
- [isSkyRT](./Env.html#isSkyRT)
- [rotation](./Env.html#rotation)
- [scene](./Env.html#scene)
- [skyMap](./Env.html#skyMap)
- [specularExp](./Env.html#specularExp)
- [specularMap](./Env.html#specularMap)
- [specularMipmapCount](./Env.html#specularMipmapCount)
- [specularMipmaps](./Env.html#specularMipmaps)
- [specularRGBD](./Env.html#specularRGBD)
- [useHalfSkyMap](./Env.html#useHalfSkyMap)
- [version](./Env.html#version)

### [#](#Methods) Methods

- [getData](./Env.html#getData)
- [setData](./Env.html#setData)
- [setDataOne](./Env.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Env**()

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
| `data` | [`IEnvData`](./../interfaces/IEnvData.html) |

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
| `data` | [`IEnvData`](./../interfaces/IEnvData.html) |

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
| `data` | [`IEnvData`](./../interfaces/IEnvData.html) |

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
| `data` | [`IEnvData`](./../interfaces/IEnvData.html) | - |

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
| `data` | [`IEnvData`](./../interfaces/IEnvData.html) |
| `preData` | [`IEnvData`](./../interfaces/IEnvData.html) |

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

详见[EnvSchema](./../modules.html#EnvSchema)。

#### [#](#Overrides) Overrides

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[] = `[]`

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[EVENTS](./Component.html#EVENTS)

## [#](#Accessors-2) Accessors

### [#](#diffuseExp) diffuseExp

• `get` **diffuseExp**(): `number`

#### [#](#Returns-6) Returns

`number`

---

### [#](#diffuseSH) diffuseSH

• `get` **diffuseSH**(): `Float32Array`

#### [#](#Returns-7) Returns

`Float32Array`

---

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-8) Returns

[`Element`](./Element.html)

---

### [#](#hasDiffuse) hasDiffuse

• `get` **hasDiffuse**(): `boolean`

#### [#](#Returns-9) Returns

`boolean`

---

### [#](#hasSpecular) hasSpecular

• `get` **hasSpecular**(): `boolean`

#### [#](#Returns-10) Returns

`boolean`

---

### [#](#isSky2D) isSky2D

• `get` **isSky2D**(): `boolean`

#### [#](#Returns-11) Returns

`boolean`

---

### [#](#isSkyRT) isSkyRT

• `get` **isSkyRT**(): `boolean`

#### [#](#Returns-12) Returns

`boolean`

---

### [#](#rotation) rotation

• `get` **rotation**(): `number`

#### [#](#Returns-13) Returns

`number`

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-14) Returns

[`Scene`](./Scene.html)

---

### [#](#skyMap) skyMap

• `get` **skyMap**(): `default`

#### [#](#Returns-15) Returns

`default`

---

### [#](#specularExp) specularExp

• `get` **specularExp**(): `number`

#### [#](#Returns-16) Returns

`number`

---

### [#](#specularMap) specularMap

• `get` **specularMap**(): `default`

#### [#](#Returns-17) Returns

`default`

---

### [#](#specularMipmapCount) specularMipmapCount

• `get` **specularMipmapCount**(): `number`

#### [#](#Returns-18) Returns

`number`

---

### [#](#specularMipmaps) specularMipmaps

• `get` **specularMipmaps**(): `boolean`

#### [#](#Returns-19) Returns

`boolean`

---

### [#](#specularRGBD) specularRGBD

• `get` **specularRGBD**(): `boolean`

#### [#](#Returns-20) Returns

`boolean`

---

### [#](#useHalfSkyMap) useHalfSkyMap

• `get` **useHalfSkyMap**(): `boolean`

#### [#](#Returns-21) Returns

`boolean`

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-22) Returns

`number`

## [#](#Methods-2) Methods

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IEnvData`](./../interfaces/IEnvData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IEnvData`](./../interfaces/IEnvData.html) |

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-23) Returns

[`IEnvData`](./../interfaces/IEnvData.html)[`T`]

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IEnvData`](./../interfaces/IEnvData.html)> |

#### [#](#Returns-24) Returns

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
| `T` | extends keyof [`IEnvData`](./../interfaces/IEnvData.html) |

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IEnvData`](./../interfaces/IEnvData.html)[`T`] |

#### [#](#Returns-25) Returns

`void`

#### [#](#Inherited-from-11) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.