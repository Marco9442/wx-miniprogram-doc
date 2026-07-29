[xr-frame](./../) / [Exports](./../modules.html) / AssetMaterial

# [#](#Class-AssetMaterial) Class: AssetMaterial

材质资源创建组件，为了在`xml`中创建[Material](./Material.html)资源，一般被代理到{@link XRAssetMaterial}元素。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IAssetMaterialData`](./../interfaces/IAssetMaterialData.html)>

  ↳ **`AssetMaterial`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./AssetMaterial.html#constructor)

### [#](#Events) Events

- [onAdd](./AssetMaterial.html#onAdd)
- [onRelease](./AssetMaterial.html#onRelease)
- [onRemove](./AssetMaterial.html#onRemove)
- [onTick](./AssetMaterial.html#onTick)
- [onUpdate](./AssetMaterial.html#onUpdate)

### [#](#Properties) Properties

- [priority](./AssetMaterial.html#priority)
- [schema](./AssetMaterial.html#schema)
- [EVENTS](./AssetMaterial.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./AssetMaterial.html#el)
- [scene](./AssetMaterial.html#scene)
- [version](./AssetMaterial.html#version)

### [#](#Methods) Methods

- [getData](./AssetMaterial.html#getData)
- [setData](./AssetMaterial.html#setData)
- [setDataOne](./AssetMaterial.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new AssetMaterial**()

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
| `data` | [`IAssetMaterialData`](./../interfaces/IAssetMaterialData.html) |

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
| `data` | [`IAssetMaterialData`](./../interfaces/IAssetMaterialData.html) |

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
| `data` | [`IAssetMaterialData`](./../interfaces/IAssetMaterialData.html) |

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
| `data` | [`IAssetMaterialData`](./../interfaces/IAssetMaterialData.html) | - |

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
| `data` | [`IAssetMaterialData`](./../interfaces/IAssetMaterialData.html) |
| `preData` | [`IAssetMaterialData`](./../interfaces/IAssetMaterialData.html) |

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

详见[AssetMaterialSchema](./../modules.html#AssetMaterialSchema)。

#### [#](#Overrides) Overrides

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

▸ **getData**<`T`>(`key`): [`IAssetMaterialData`](./../interfaces/IAssetMaterialData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IAssetMaterialData`](./../interfaces/IAssetMaterialData.html) |

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-9) Returns

[`IAssetMaterialData`](./../interfaces/IAssetMaterialData.html)[`T`]

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IAssetMaterialData`](./../interfaces/IAssetMaterialData.html)> |

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
| `T` | extends keyof [`IAssetMaterialData`](./../interfaces/IAssetMaterialData.html) |

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IAssetMaterialData`](./../interfaces/IAssetMaterialData.html)[`T`] |

#### [#](#Returns-11) Returns

`void`

#### [#](#Inherited-from-11) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.