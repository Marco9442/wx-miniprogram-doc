[xr-frame](./../) / [Exports](./../modules.html) / RenderSystem

# [#](#Class-RenderSystem) Class: RenderSystem

渲染系统，负责整个场景渲染的管理。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IRenderSystemData`](./../interfaces/IRenderSystemData.html)>

  ↳ **`RenderSystem`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./RenderSystem.html#constructor)

### [#](#Events) Events

- [onAdd](./RenderSystem.html#onAdd)
- [onRelease](./RenderSystem.html#onRelease)
- [onRemove](./RenderSystem.html#onRemove)
- [onTick](./RenderSystem.html#onTick)
- [onUpdate](./RenderSystem.html#onUpdate)

### [#](#Properties) Properties

- [priority](./RenderSystem.html#priority)
- [schema](./RenderSystem.html#schema)
- [EVENTS](./RenderSystem.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./RenderSystem.html#el)
- [renderGraph](./RenderSystem.html#renderGraph)
- [scene](./RenderSystem.html#scene)
- [shadowColor](./RenderSystem.html#shadowColor)
- [version](./RenderSystem.html#version)

### [#](#Methods) Methods

- [changeFeatures](./RenderSystem.html#changeFeatures)
- [changeMacros](./RenderSystem.html#changeMacros)
- [disableInstance](./RenderSystem.html#disableInstance)
- [enableInstance](./RenderSystem.html#enableInstance)
- [getData](./RenderSystem.html#getData)
- [getFeature](./RenderSystem.html#getFeature)
- [getMacro](./RenderSystem.html#getMacro)
- [setData](./RenderSystem.html#setData)
- [setDataOne](./RenderSystem.html#setDataOne)
- [useRenderGraph](./RenderSystem.html#useRenderGraph)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new RenderSystem**()

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
| `data` | [`IRenderSystemData`](./../interfaces/IRenderSystemData.html) |

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
| `data` | [`IRenderSystemData`](./../interfaces/IRenderSystemData.html) |

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
| `data` | [`IRenderSystemData`](./../interfaces/IRenderSystemData.html) |

#### [#](#Returns-3) Returns

`void`

#### [#](#Inherited-from-4) Inherited from

[Component](./Component.html).[onRemove](./Component.html#onRemove)

---

### [#](#onTick) onTick

▸ **onTick**(): `void`

渲染每帧触发的回调。

#### [#](#Returns-4) Returns

`void`

#### [#](#Inherited-from-5) Inherited from

[Component](./Component.html).[onTick](./Component.html#onTick)

---

### [#](#onUpdate) onUpdate

▸ **onUpdate**(`data`, `preData`): `void`

数据更新时触发的回调。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IRenderSystemData`](./../interfaces/IRenderSystemData.html) |
| `preData` | [`IRenderSystemData`](./../interfaces/IRenderSystemData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number` = `400`

自定义组件的更新优先级。

#### [#](#Overrides) Overrides

[Component](./Component.html).[priority](./Component.html#priority)

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html)

详见[RenderSystemSchema](./../modules.html#RenderSystemSchema)。

#### [#](#Overrides-2) Overrides

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[] = `[]`

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[EVENTS](./Component.html#EVENTS)

## [#](#Accessors-2) Accessors

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-6) Returns

[`Element`](./Element.html)

---

### [#](#renderGraph) renderGraph

• `get` **renderGraph**(): `default`<`any`>

当前正在使用的RenderGraph。

#### [#](#Returns-7) Returns

`default`<`any`>

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-8) Returns

[`Scene`](./Scene.html)

---

### [#](#shadowColor) shadowColor

• `get` **shadowColor**(): `number`[]

#### [#](#Returns-9) Returns

`number`[]

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-10) Returns

`number`

## [#](#Methods-2) Methods

### [#](#changeFeatures) changeFeatures

▸ **changeFeatures**(`features`): `void`

修改全局渲染特性。

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `features` | `Object` |

#### [#](#Returns-11) Returns

`void`

---

### [#](#changeMacros) changeMacros

▸ **changeMacros**(`macros`): `void`

修改全局宏信息。

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `macros` | `Object` |

#### [#](#Returns-12) Returns

`void`

---

### [#](#disableInstance) disableInstance

▸ **disableInstance**(): `void`

关闭全局GPU实例化。

#### [#](#Returns-13) Returns

`void`

---

### [#](#enableInstance) enableInstance

▸ **enableInstance**(): `void`

开启全局GPU实例化。

#### [#](#Returns-14) Returns

`void`

---

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IRenderSystemData`](./../interfaces/IRenderSystemData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IRenderSystemData`](./../interfaces/IRenderSystemData.html) |

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-15) Returns

[`IRenderSystemData`](./../interfaces/IRenderSystemData.html)[`T`]

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#getFeature) getFeature

▸ **getFeature**(`key`): `string` | `number` | `boolean`

获取全局渲染特性。

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |

#### [#](#Returns-16) Returns

`string` | `number` | `boolean`

---

### [#](#getMacro) getMacro

▸ **getMacro**(`key`): `string` | `number` | `boolean`

获取全局宏信息。

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |

#### [#](#Returns-17) Returns

`string` | `number` | `boolean`

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IRenderSystemData`](./../interfaces/IRenderSystemData.html)> |

#### [#](#Returns-18) Returns

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
| `T` | extends keyof [`IRenderSystemData`](./../interfaces/IRenderSystemData.html) |

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IRenderSystemData`](./../interfaces/IRenderSystemData.html)[`T`] |

#### [#](#Returns-19) Returns

`void`

#### [#](#Inherited-from-10) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

---

### [#](#useRenderGraph) useRenderGraph

▸ **useRenderGraph**(`rg`): `void`

使用某个RenderGraph，默认会使用内置的`ForwardBaseRG`。

#### [#](#Parameters-12) Parameters

| Name | Type |
| --- | --- |
| `rg` | `default`<`any`> |

#### [#](#Returns-20) Returns

`void`

Incorrect translation.