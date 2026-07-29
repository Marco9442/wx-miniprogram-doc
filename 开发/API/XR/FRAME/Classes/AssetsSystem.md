[xr-frame](./../) / [Exports](./../modules.html) / AssetsSystem

# [#](#Class-AssetsSystem) Class: AssetsSystem

资源系统，负责整个场景的资源管理。

一般不需要手动管理，而是利用[AssetLoad](./AssetLoad.html)、[registerGeometry](./../modules.html#registerGeometry)之类的使用。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IAssetsSystemData`](./../interfaces/IAssetsSystemData.html)>

  ↳ **`AssetsSystem`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./AssetsSystem.html#constructor)

### [#](#Events) Events

- [onAdd](./AssetsSystem.html#onAdd)
- [onRelease](./AssetsSystem.html#onRelease)
- [onRemove](./AssetsSystem.html#onRemove)
- [onTick](./AssetsSystem.html#onTick)
- [onUpdate](./AssetsSystem.html#onUpdate)

### [#](#Properties) Properties

- [priority](./AssetsSystem.html#priority)
- [schema](./AssetsSystem.html#schema)
- [EVENTS](./AssetsSystem.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./AssetsSystem.html#el)
- [scene](./AssetsSystem.html#scene)
- [version](./AssetsSystem.html#version)

### [#](#Methods) Methods

- [addAsset](./AssetsSystem.html#addAsset)
- [cancelAsset](./AssetsSystem.html#cancelAsset)
- [getAsset](./AssetsSystem.html#getAsset)
- [getAssetWithState](./AssetsSystem.html#getAssetWithState)
- [getData](./AssetsSystem.html#getData)
- [loadAsset](./AssetsSystem.html#loadAsset)
- [releaseAsset](./AssetsSystem.html#releaseAsset)
- [setData](./AssetsSystem.html#setData)
- [setDataOne](./AssetsSystem.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new AssetsSystem**()

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
| `data` | [`IAssetsSystemData`](./../interfaces/IAssetsSystemData.html) |

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
| `data` | [`IAssetsSystemData`](./../interfaces/IAssetsSystemData.html) |

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
| `data` | [`IAssetsSystemData`](./../interfaces/IAssetsSystemData.html) |

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
| `data` | [`IAssetsSystemData`](./../interfaces/IAssetsSystemData.html) | - |

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
| `data` | [`IAssetsSystemData`](./../interfaces/IAssetsSystemData.html) |
| `preData` | [`IAssetsSystemData`](./../interfaces/IAssetsSystemData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number` = `10`

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

### [#](#addAsset) addAsset

▸ **addAsset**<`T`>(`type`, `id`, `asset`): `void`

手动添加一个资源。

#### [#](#Type-parameters) Type parameters

| Name |
| --- |
| `T` |

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |
| `id` | `string` |
| `asset` | `T` |

#### [#](#Returns-9) Returns

`void`

---

### [#](#cancelAsset) cancelAsset

▸ **cancelAsset**(`type`, `id`): `void`

取消加载一个资源。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |
| `id` | `string` |

#### [#](#Returns-10) Returns

`void`

---

### [#](#getAsset) getAsset

▸ **getAsset**<`T`>(`type`, `id`, `fallback?`): `T`

获取一个资源，如果尚未加载完成，也会返回`undefined`。

#### [#](#Type-parameters-2) Type parameters

| Name |
| --- |
| `T` |

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |
| `id` | `string` |
| `fallback?` | `string` |

#### [#](#Returns-11) Returns

`T`

---

### [#](#getAssetWithState) getAssetWithState

▸ **getAssetWithState**<`T`>(`type`, `id`, `fallback?`): `IAssetWithState`<`T`>

获取一个资源以及加载状态。

#### [#](#Type-parameters-3) Type parameters

| Name |
| --- |
| `T` |

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |
| `id` | `string` |
| `fallback?` | `string` |

#### [#](#Returns-12) Returns

`IAssetWithState`<`T`>

---

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IAssetsSystemData`](./../interfaces/IAssetsSystemData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters-4) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends `never` |

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-13) Returns

[`IAssetsSystemData`](./../interfaces/IAssetsSystemData.html)[`T`]

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#loadAsset) loadAsset

▸ **loadAsset**(`params`, `parent?`): `Promise`<`IAssetWithState`<`any`>>

手动加载一个资源。

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `params` | `IAssetLoadData`<`any`> |
| `parent?` | [`Element`](./Element.html) |

#### [#](#Returns-14) Returns

`Promise`<`IAssetWithState`<`any`>>

---

### [#](#releaseAsset) releaseAsset

▸ **releaseAsset**(`type`, `id`): `void`

手动释放一个资源。

注意在`xml`里加载的资源不要手动释放。

#### [#](#Parameters-12) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |
| `id` | `string` |

#### [#](#Returns-15) Returns

`void`

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-13) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IAssetsSystemData`](./../interfaces/IAssetsSystemData.html)> |

#### [#](#Returns-16) Returns

`void`

#### [#](#Inherited-from-10) Inherited from

[Component](./Component.html).[setData](./Component.html#setData)

---

### [#](#setDataOne) setDataOne

▸ **setDataOne**<`T`>(`key`, `value`): `void`

设置一个数据。

#### [#](#Type-parameters-5) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends `never` |

#### [#](#Parameters-14) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IAssetsSystemData`](./../interfaces/IAssetsSystemData.html)[`T`] |

#### [#](#Returns-17) Returns

`void`

#### [#](#Inherited-from-11) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.