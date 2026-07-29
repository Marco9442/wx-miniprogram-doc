[xr-frame](./../) / [Exports](./../modules.html) / Camera

# [#](#Class-Camera) Class: Camera

相机组件，一般被代理到[XRCamera](./XRCamera.html)元素。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`ICameraData`](./../interfaces/ICameraData.html)>

  ↳ **`Camera`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Camera.html#constructor)

### [#](#Events) Events

- [onAdd](./Camera.html#onAdd)
- [onRelease](./Camera.html#onRelease)
- [onRemove](./Camera.html#onRemove)
- [onTick](./Camera.html#onTick)
- [onUpdate](./Camera.html#onUpdate)

### [#](#Properties) Properties

- [priority](./Camera.html#priority)
- [schema](./Camera.html#schema)
- [EVENTS](./Camera.html#EVENTS)

### [#](#Accessors) Accessors

- [allowFeatures](./Camera.html#allowFeatures)
- [background](./Camera.html#background)
- [bgStates](./Camera.html#bgStates)
- [bgStatesClear](./Camera.html#bgStatesClear)
- [cullMask](./Camera.html#cullMask)
- [depth](./Camera.html#depth)
- [el](./Camera.html#el)
- [far](./Camera.html#far)
- [features](./Camera.html#features)
- [hdr](./Camera.html#hdr)
- [near](./Camera.html#near)
- [postProcess](./Camera.html#postProcess)
- [scene](./Camera.html#scene)
- [target](./Camera.html#target)
- [version](./Camera.html#version)

### [#](#Methods) Methods

- [changeProjectMatrix](./Camera.html#changeProjectMatrix)
- [changeViewMatrix](./Camera.html#changeViewMatrix)
- [clearBackgroundRenderStates](./Camera.html#clearBackgroundRenderStates)
- [convertClipPositionToWorld](./Camera.html#convertClipPositionToWorld)
- [convertWorldPositionToClip](./Camera.html#convertWorldPositionToClip)
- [getData](./Camera.html#getData)
- [setBackgroundRenderStates](./Camera.html#setBackgroundRenderStates)
- [setData](./Camera.html#setData)
- [setDataOne](./Camera.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Camera**()

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
| `data` | [`ICameraData`](./../interfaces/ICameraData.html) |

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
| `data` | [`ICameraData`](./../interfaces/ICameraData.html) |

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
| `data` | [`ICameraData`](./../interfaces/ICameraData.html) |

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
| `data` | [`ICameraData`](./../interfaces/ICameraData.html) |

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
| `data` | [`ICameraData`](./../interfaces/ICameraData.html) |
| `preData` | [`ICameraData`](./../interfaces/ICameraData.html) |

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

详见[CameraSchema](./../modules.html#CameraSchema)。

#### [#](#Overrides-2) Overrides

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[] = `[]`

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[EVENTS](./Component.html#EVENTS)

## [#](#Accessors-2) Accessors

### [#](#allowFeatures) allowFeatures

• `get` **allowFeatures**(): `string`[]

#### [#](#Returns-6) Returns

`string`[]

---

### [#](#background) background

• `get` **background**(): [`TCameraBackground`](./../modules.html#TCameraBackground)

#### [#](#Returns-7) Returns

[`TCameraBackground`](./../modules.html#TCameraBackground)

---

### [#](#bgStates) bgStates

• `get` **bgStates**(): `Object`

**`internal。`**

#### [#](#Returns-8) Returns

`Object`

---

### [#](#bgStatesClear) bgStatesClear

• `get` **bgStatesClear**(): `boolean`

**`internal。`**

#### [#](#Returns-9) Returns

`boolean`

---

### [#](#cullMask) cullMask

• `get` **cullMask**(): `number`

#### [#](#Returns-10) Returns

`number`

---

### [#](#depth) depth

• `get` **depth**(): `number`

相机深度。

#### [#](#Returns-11) Returns

`number`

---

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-12) Returns

[`Element`](./Element.html)

---

### [#](#far) far

• `get` **far**(): `number`

#### [#](#Returns-13) Returns

`number`

---

### [#](#features) features

• `get` **features**(): `Object`

当前渲染特性集合。

#### [#](#Returns-14) Returns

`Object`

---

### [#](#hdr) hdr

• `get` **hdr**(): `boolean`

#### [#](#Returns-15) Returns

`boolean`

---

### [#](#near) near

• `get` **near**(): `number`

#### [#](#Returns-16) Returns

`number`

---

### [#](#postProcess) postProcess

• `get` **postProcess**(): [`PostProcess`](./PostProcess.html)[]

#### [#](#Returns-17) Returns

[`PostProcess`](./PostProcess.html)[]

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-18) Returns

[`Scene`](./Scene.html)

---

### [#](#target) target

• `get` **target**(): [`Transform`](./Transform.html)

#### [#](#Returns-19) Returns

[`Transform`](./Transform.html)

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-20) Returns

`number`

## [#](#Methods-2) Methods

### [#](#changeProjectMatrix) changeProjectMatrix

▸ **changeProjectMatrix**(`manual`, `mat4?`): `void`

修改projectMatrix的设置类型。

#### [#](#Parameters-6) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `manual` | `boolean` | 是否要设置为手动模式。 |
| `mat4?` | `Float32Array` | [`Matrix4`](./Matrix4.html) | 手动模式下，要设置的值。 |

#### [#](#Returns-21) Returns

`void`

---

### [#](#changeViewMatrix) changeViewMatrix

▸ **changeViewMatrix**(`manual`, `mat4?`): `void`

修改viewMatrix的设置类型。

#### [#](#Parameters-7) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `manual` | `boolean` | 是否要设置为手动模式。 |
| `mat4?` | `Float32Array` | [`Matrix4`](./Matrix4.html) | 手动模式下，要设置的值。 |

#### [#](#Returns-22) Returns

`void`

---

### [#](#clearBackgroundRenderStates) clearBackgroundRenderStates

▸ **clearBackgroundRenderStates**(): `void`

清空相机背景渲染状态。

#### [#](#Returns-23) Returns

`void`

---

### [#](#convertClipPositionToWorld) convertClipPositionToWorld

▸ **convertClipPositionToWorld**(`clipPos`, `dst?`): [`Vector3`](./Vector3.html)

将齐次裁剪空间转换到世界坐标系位置。

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `clipPos` | [`Vector3`](./Vector3.html) |
| `dst?` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-24) Returns

[`Vector3`](./Vector3.html)

---

### [#](#convertWorldPositionToClip) convertWorldPositionToClip

▸ **convertWorldPositionToClip**(`worldPos`, `dst?`): [`Vector3`](./Vector3.html)

将世界坐标系位置转换到齐次裁剪空间。

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `worldPos` | [`Vector3`](./Vector3.html) |
| `dst?` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-25) Returns

[`Vector3`](./Vector3.html)

---

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`ICameraData`](./../interfaces/ICameraData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`ICameraData`](./../interfaces/ICameraData.html) |

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-26) Returns

[`ICameraData`](./../interfaces/ICameraData.html)[`T`]

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#setBackgroundRenderStates) setBackgroundRenderStates

▸ **setBackgroundRenderStates**(`states`): `void`

修改相机背景的渲染状态。

#### [#](#Parameters-11) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `states` | `Object` | 同[Material.setRenderStates](./Material.html#setRenderStates) |

#### [#](#Returns-27) Returns

`void`

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-12) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`ICameraData`](./../interfaces/ICameraData.html)> |

#### [#](#Returns-28) Returns

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
| `T` | extends keyof [`ICameraData`](./../interfaces/ICameraData.html) |

#### [#](#Parameters-13) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`ICameraData`](./../interfaces/ICameraData.html)[`T`] |

#### [#](#Returns-29) Returns

`void`

#### [#](#Inherited-from-10) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.