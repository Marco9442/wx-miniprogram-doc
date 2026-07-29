[xr-frame](./../) / [Exports](./../modules.html) / GLTF

# [#](#Class-GLTF) Class: GLTF

将一个[GLTF模型](./GLTFModel.html)实例化并渲染出来。
[xr-gltf](./XRGLTF.html)标签会自动生成该组件。

> 会在当前元素下新建一系列子元素，作为GLTF模型的每个场景的根节点。
> 会在当前元素上新建[Animator](./Animator.html)组件，并向其添加实例化生成的动画片段。

**`see`** [IGLTFData](./../interfaces/IGLTFData.html)

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IGLTFData`](./../interfaces/IGLTFData.html)>

  ↳ **`GLTF`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./GLTF.html#constructor)

### [#](#Events) Events

- [onAdd](./GLTF.html#onAdd)
- [onRelease](./GLTF.html#onRelease)
- [onRemove](./GLTF.html#onRemove)
- [onTick](./GLTF.html#onTick)
- [onUpdate](./GLTF.html#onUpdate)

### [#](#Properties) Properties

- [priority](./GLTF.html#priority)
- [schema](./GLTF.html#schema)
- [EVENTS](./GLTF.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./GLTF.html#el)
- [meshes](./GLTF.html#meshes)
- [scene](./GLTF.html#scene)
- [version](./GLTF.html#version)

### [#](#Methods) Methods

- [calcTotalBoundBox](./GLTF.html#calcTotalBoundBox)
- [getData](./GLTF.html#getData)
- [getInternalNodeByName](./GLTF.html#getInternalNodeByName)
- [getPrimitivesByMeshName](./GLTF.html#getPrimitivesByMeshName)
- [getPrimitivesByNodeName](./GLTF.html#getPrimitivesByNodeName)
- [setData](./GLTF.html#setData)
- [setDataOne](./GLTF.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new GLTF**()

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
| `data` | [`IGLTFData`](./../interfaces/IGLTFData.html) |

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
| `data` | [`IGLTFData`](./../interfaces/IGLTFData.html) |

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
| `data` | [`IGLTFData`](./../interfaces/IGLTFData.html) |

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
| `data` | [`IGLTFData`](./../interfaces/IGLTFData.html) | - |

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
| `data` | [`IGLTFData`](./../interfaces/IGLTFData.html) |
| `preData` | [`IGLTFData`](./../interfaces/IGLTFData.html) |

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

▪ `Static` **EVENTS**: `string`[]

#### [#](#Overrides-3) Overrides

[Component](./Component.html).[EVENTS](./Component.html#EVENTS)

## [#](#Accessors-2) Accessors

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-6) Returns

[`Element`](./Element.html)

---

### [#](#meshes) meshes

• `get` **meshes**(): [`Mesh`](./Mesh.html)[]

获取GLTF模型实例化过程中生成的所有[Mesh](./Mesh.html)组件。

#### [#](#Returns-7) Returns

[`Mesh`](./Mesh.html)[]

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-8) Returns

[`Scene`](./Scene.html)

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-9) Returns

`number`

## [#](#Methods-2) Methods

### [#](#calcTotalBoundBox) calcTotalBoundBox

▸ **calcTotalBoundBox**(): [`BoundBox`](./BoundBox.html)

计算GLTF模型整体的包围盒，返回**模型空间**内的计算结果。
每次调用都会重新计算。

#### [#](#Returns-10) Returns

[`BoundBox`](./BoundBox.html)

---

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IGLTFData`](./../interfaces/IGLTFData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IGLTFData`](./../interfaces/IGLTFData.html) |

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-11) Returns

[`IGLTFData`](./../interfaces/IGLTFData.html)[`T`]

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#getInternalNodeByName) getInternalNodeByName

▸ **getInternalNodeByName**(`name`): [`Element`](./Element.html)

根据GLTF模型中节点的`name`字段来获取内部元素。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `name` | `string` |

#### [#](#Returns-12) Returns

[`Element`](./Element.html)

---

### [#](#getPrimitivesByMeshName) getPrimitivesByMeshName

▸ **getPrimitivesByMeshName**(`name`): { `nodeName`: `string` ; `primitives`: [`Mesh`](./Mesh.html)[] }[]

根据GLTF模型中Mesh节点的`name`字段，来获取引用了该Mesh的**所有**Node节点下的所有Primitive。
在xr-frame实现中，每个引用了该Mesh的GLTFNode节点拥有**独立**的一份Primitives副本，**每个**Node节点下的**每个**Primitive对应一个`xr-frame Mesh组件`。
\**如果没有引用了该Mesh的Node节点，会返回空数组。*

#### [#](#Parameters-8) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `name` | `string` | Mesh节点的`name` |

#### [#](#Returns-13) Returns

{ `nodeName`: `string` ; `primitives`: [`Mesh`](./Mesh.html)[] }[]

一个数组，数组中的一个元素对应一个引用了该Mesh的GLTFNode节点，元素中nodeName为GLTFNode节点的`name`字段。

---

### [#](#getPrimitivesByNodeName) getPrimitivesByNodeName

▸ **getPrimitivesByNodeName**(`name`): [`Mesh`](./Mesh.html)[]

根据GLTF模型中**引用**了Mesh的**Node节点**的`name`字段，来获取对应Mesh下的所有Primitive。
一个GLTF模型中的Primitive节点对应返回中的一个`xr-frame Mesh组件`实例。
\**如果没有该名字的节点，或者节点未引用Mesh，会返回空数组。*

#### [#](#Parameters-9) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `name` | `string` | Node节点的`name`（而非Mesh节点） |

#### [#](#Returns-14) Returns

[`Mesh`](./Mesh.html)[]

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IGLTFData`](./../interfaces/IGLTFData.html)> |

#### [#](#Returns-15) Returns

`void`

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[setData](./Component.html#setData)

---

### [#](#setDataOne) setDataOne

▸ **setDataOne**<`T`>(`key`, `value`): `void`

设置一个数据。

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IGLTFData`](./../interfaces/IGLTFData.html) |

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IGLTFData`](./../interfaces/IGLTFData.html)[`T`] |

#### [#](#Returns-16) Returns

`void`

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.