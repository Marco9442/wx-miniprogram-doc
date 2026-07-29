[xr-frame](./../) / [Exports](./../modules.html) / AssetRenderTexture

# [#](#Class-AssetRenderTexture) Class: AssetRenderTexture

渲染纹理创建组件，用于在`xml`中创建[RenderTexture](./RenderTexture.html)资源，一般被代理到[XRAssetRenderTexture](./XRAssetRenderTexture.html)元素。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IAssetRenderTextureData`](./../interfaces/IAssetRenderTextureData.html)>

  ↳ **`AssetRenderTexture`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./AssetRenderTexture.html#constructor)

### [#](#Events) Events

- [onAdd](./AssetRenderTexture.html#onAdd)
- [onRelease](./AssetRenderTexture.html#onRelease)
- [onRemove](./AssetRenderTexture.html#onRemove)
- [onTick](./AssetRenderTexture.html#onTick)
- [onUpdate](./AssetRenderTexture.html#onUpdate)

### [#](#Properties) Properties

- [isAssetRenderTexture](./AssetRenderTexture.html#isAssetRenderTexture)
- [priority](./AssetRenderTexture.html#priority)
- [schema](./AssetRenderTexture.html#schema)
- [EVENTS](./AssetRenderTexture.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./AssetRenderTexture.html#el)
- [scene](./AssetRenderTexture.html#scene)
- [version](./AssetRenderTexture.html#version)

### [#](#Methods) Methods

- [getData](./AssetRenderTexture.html#getData)
- [setData](./AssetRenderTexture.html#setData)
- [setDataOne](./AssetRenderTexture.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new AssetRenderTexture**()

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
| `data` | [`IAssetRenderTextureData`](./../interfaces/IAssetRenderTextureData.html) |

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
| `data` | [`IAssetRenderTextureData`](./../interfaces/IAssetRenderTextureData.html) |

#### [#](#Returns-2) Returns

`void`

#### [#](#Inherited-from-3) Inherited from

[Component](./Component.html).[onRelease](./Component.html#onRelease)

---

### [#](#onRemove) onRemove

▸ **onRemove**(`parent`, `data`): `void`

移除AssetRenderTexture。

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `parent` | [`Element`](./Element.html) |
| `data` | [`IAssetRenderTextureData`](./../interfaces/IAssetRenderTextureData.html) |

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
| `data` | [`IAssetRenderTextureData`](./../interfaces/IAssetRenderTextureData.html) | - |

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
| `data` | [`IAssetRenderTextureData`](./../interfaces/IAssetRenderTextureData.html) |
| `preData` | [`IAssetRenderTextureData`](./../interfaces/IAssetRenderTextureData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#isAssetRenderTexture) isAssetRenderTexture

• `Readonly` **isAssetRenderTexture**: `boolean` = `true`

---

### [#](#priority) priority

• `Readonly` **priority**: `number`

自定义组件的更新优先级。

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[priority](./Component.html#priority)

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html)

详见[AssetRenderTextureSchema](./../modules.html#AssetRenderTextureSchema)。

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

▸ **getData**<`T`>(`key`): [`IAssetRenderTextureData`](./../interfaces/IAssetRenderTextureData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IAssetRenderTextureData`](./../interfaces/IAssetRenderTextureData.html) |

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-9) Returns

[`IAssetRenderTextureData`](./../interfaces/IAssetRenderTextureData.html)[`T`]

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IAssetRenderTextureData`](./../interfaces/IAssetRenderTextureData.html)> |

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
| `T` | extends keyof [`IAssetRenderTextureData`](./../interfaces/IAssetRenderTextureData.html) |

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IAssetRenderTextureData`](./../interfaces/IAssetRenderTextureData.html)[`T`] |

#### [#](#Returns-11) Returns

`void`

#### [#](#Inherited-from-11) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.