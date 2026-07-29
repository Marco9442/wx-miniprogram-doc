[xr-frame](./../) / [Exports](./../modules.html) / Text

# [#](#Class-Text) Class: Text

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`ITextData`](./../interfaces/ITextData.html)>

  ↳ **`Text`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Text.html#constructor)

### [#](#Events) Events

- [onAdd](./Text.html#onAdd)
- [onRelease](./Text.html#onRelease)
- [onRemove](./Text.html#onRemove)
- [onTick](./Text.html#onTick)
- [onUpdate](./Text.html#onUpdate)

### [#](#Properties) Properties

- [priority](./Text.html#priority)
- [schema](./Text.html#schema)
- [EVENTS](./Text.html#EVENTS)
- [FillRenderData](./Text.html#FillRenderData)
- [QueryGlyphs](./Text.html#QueryGlyphs)
- [Typesetting](./Text.html#Typesetting)

### [#](#Accessors) Accessors

- [el](./Text.html#el)
- [id](./Text.html#id)
- [scene](./Text.html#scene)
- [version](./Text.html#version)

### [#](#Methods) Methods

- [getData](./Text.html#getData)
- [setData](./Text.html#setData)
- [setDataOne](./Text.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Text**()

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
| `data` | [`ITextData`](./../interfaces/ITextData.html) |

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
| `data` | [`ITextData`](./../interfaces/ITextData.html) |

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
| `data` | [`ITextData`](./../interfaces/ITextData.html) |

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
| `data` | [`ITextData`](./../interfaces/ITextData.html) |

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
| `data` | [`ITextData`](./../interfaces/ITextData.html) |
| `preData` | [`ITextData`](./../interfaces/ITextData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number` = `300`

自定义组件的更新优先级。

#### [#](#Overrides) Overrides

[Component](./Component.html).[priority](./Component.html#priority)

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html)

自定义组件的`schema`。

#### [#](#Overrides-2) Overrides

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[] = `[]`

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[EVENTS](./Component.html#EVENTS)

---

### [#](#FillRenderData) FillRenderData

▪ `Static` **FillRenderData**: (`vertexF32`: `Float32Array`, `indexU16`: `Uint16Array`, `batchArray`: `ICharacterData`[]) => `void`

#### [#](#Type-declaration) Type declaration

▸ (`vertexF32`, `indexU16`, `batchArray`): `void`

##### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `vertexF32` | `Float32Array` |
| `indexU16` | `Uint16Array` |
| `batchArray` | `ICharacterData`[] |

##### [#](#Returns-6) Returns

`void`

---

### [#](#QueryGlyphs) QueryGlyphs

▪ `Static` **QueryGlyphs**: (`scene`: [`Scene`](./Scene.html), `characters`: `string`, `italic`: `boolean`, `bold`: `boolean`, `fontSize`: `number`, `fontFamily`: `string`) => `IGlyph`[]

#### [#](#Type-declaration-2) Type declaration

▸ (`scene`, `characters`, `italic`, `bold`, `fontSize`, `fontFamily`): `IGlyph`[]

多字客户端纹理请求接口

##### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `scene` | [`Scene`](./Scene.html) |
| `characters` | `string` |
| `italic` | `boolean` |
| `bold` | `boolean` |
| `fontSize` | `number` |
| `fontFamily` | `string` |

##### [#](#Returns-7) Returns

`IGlyph`[]

---

### [#](#Typesetting) Typesetting

▪ `Static` **Typesetting**: (`glyphs`: `IGlyph`[], `batchArrays`: `ICharacterData`[][], `batchIndexs`: `number`[], `wrapWidth`: `number`, `wrapHeight`: `number`, `lineHeight`: `number`, `anchor`: `number`[], `padding`: `number`[], `vertAlign`: `EVertAlignment`, `horzAlign`: `EHorzAlignment`) => `void`

#### [#](#Type-declaration-3) Type declaration

▸ (`glyphs`, `batchArrays`, `batchIndexs`, `wrapWidth`, `wrapHeight`, `lineHeight`, `anchor`, `padding`, `vertAlign`, `horzAlign`): `void`

##### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `glyphs` | `IGlyph`[] |
| `batchArrays` | `ICharacterData`[][] |
| `batchIndexs` | `number`[] |
| `wrapWidth` | `number` |
| `wrapHeight` | `number` |
| `lineHeight` | `number` |
| `anchor` | `number`[] |
| `padding` | `number`[] |
| `vertAlign` | `EVertAlignment` |
| `horzAlign` | `EHorzAlignment` |

##### [#](#Returns-8) Returns

`void`

## [#](#Accessors-2) Accessors

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-9) Returns

[`Element`](./Element.html)

---

### [#](#id) id

• `get` **id**(): `number`

#### [#](#Returns-10) Returns

`number`

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-11) Returns

[`Scene`](./Scene.html)

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-12) Returns

`number`

## [#](#Methods-2) Methods

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`ITextData`](./../interfaces/ITextData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`ITextData`](./../interfaces/ITextData.html) |

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-13) Returns

[`ITextData`](./../interfaces/ITextData.html)[`T`]

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`ITextData`](./../interfaces/ITextData.html)> |

#### [#](#Returns-14) Returns

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
| `T` | extends keyof [`ITextData`](./../interfaces/ITextData.html) |

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`ITextData`](./../interfaces/ITextData.html)[`T`] |

#### [#](#Returns-15) Returns

`void`

#### [#](#Inherited-from-10) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.