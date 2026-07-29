[xr-frame](./../) / [Exports](./../modules.html) / Assets

# [#](#Class-Assets) Class: Assets

资源加载组组件，会统计作为其子节点的[AssetLoad](./AssetLoad.html)组件的加载状态，派发事件。
一般被代理到[XRAssets](./XRAssets.html)元素。

事件`progress`会在资源加载进度更新时触发，值为`{progress: number, asset: IAssetLoadData}`。
事件`loaded`会在所有资源加载完成是触发，值为`{assets: {[key: string]: IAssetLoadData}, errors: {[key: string]: Error}}`。
详见{@link IAssetLoadData}。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IAssetsData`](./../interfaces/IAssetsData.html)>

  ↳ **`Assets`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Assets.html#constructor)

### [#](#Events) Events

- [onAdd](./Assets.html#onAdd)
- [onRelease](./Assets.html#onRelease)
- [onRemove](./Assets.html#onRemove)
- [onTick](./Assets.html#onTick)
- [onUpdate](./Assets.html#onUpdate)

### [#](#Properties) Properties

- [priority](./Assets.html#priority)
- [schema](./Assets.html#schema)
- [EVENTS](./Assets.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./Assets.html#el)
- [scene](./Assets.html#scene)
- [version](./Assets.html#version)

### [#](#Methods) Methods

- [getData](./Assets.html#getData)
- [setData](./Assets.html#setData)
- [setDataOne](./Assets.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Assets**()

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
| `data` | [`IAssetsData`](./../interfaces/IAssetsData.html) |

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
| `data` | [`IAssetsData`](./../interfaces/IAssetsData.html) |

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
| `data` | [`IAssetsData`](./../interfaces/IAssetsData.html) |

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
| `data` | [`IAssetsData`](./../interfaces/IAssetsData.html) | - |

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
| `data` | [`IAssetsData`](./../interfaces/IAssetsData.html) |
| `preData` | [`IAssetsData`](./../interfaces/IAssetsData.html) |

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

自定义组件的`schema`。

#### [#](#Overrides) Overrides

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[]

#### [#](#Overrides-2) Overrides

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

▸ **getData**<`T`>(`key`): [`IAssetsData`](./../interfaces/IAssetsData.html)[`T`]

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

[`IAssetsData`](./../interfaces/IAssetsData.html)[`T`]

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IAssetsData`](./../interfaces/IAssetsData.html)> |

#### [#](#Returns-10) Returns

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
| `T` | extends `never` |

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IAssetsData`](./../interfaces/IAssetsData.html)[`T`] |

#### [#](#Returns-11) Returns

`void`

#### [#](#Inherited-from-10) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.