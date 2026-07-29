[xr-frame](./../) / [Exports](./../modules.html) / Transform

# [#](#Class-Transform) Class: Transform

3D变换组件，作为场景中3D节点的根基，一般被代理到[XRNode](./XRNode.html)元素。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`ITransformData`](./../interfaces/ITransformData.html)>

  ↳ **`Transform`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Transform.html#constructor)

### [#](#Events) Events

- [onAdd](./Transform.html#onAdd)
- [onRelease](./Transform.html#onRelease)
- [onRemove](./Transform.html#onRemove)
- [onTick](./Transform.html#onTick)
- [onUpdate](./Transform.html#onUpdate)

### [#](#Properties) Properties

- [priority](./Transform.html#priority)
- [schema](./Transform.html#schema)
- [EVENTS](./Transform.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./Transform.html#el)
- [layer](./Transform.html#layer)
- [node](./Transform.html#node)
- [position](./Transform.html#position)
- [quaternion](./Transform.html#quaternion)
- [rotation](./Transform.html#rotation)
- [scale](./Transform.html#scale)
- [scene](./Transform.html#scene)
- [version](./Transform.html#version)
- [visible](./Transform.html#visible)
- [worldForward](./Transform.html#worldForward)
- [worldMatrix](./Transform.html#worldMatrix)
- [worldPosition](./Transform.html#worldPosition)
- [worldQuaternion](./Transform.html#worldQuaternion)
- [worldRight](./Transform.html#worldRight)
- [worldScale](./Transform.html#worldScale)
- [worldUp](./Transform.html#worldUp)

### [#](#Methods) Methods

- [getData](./Transform.html#getData)
- [setData](./Transform.html#setData)
- [setDataOne](./Transform.html#setDataOne)
- [setLocalMatrix](./Transform.html#setLocalMatrix)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Transform**()

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
| `data` | [`ITransformData`](./../interfaces/ITransformData.html) |

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
| `data` | [`ITransformData`](./../interfaces/ITransformData.html) |

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
| `data` | [`ITransformData`](./../interfaces/ITransformData.html) |

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
| `data` | [`ITransformData`](./../interfaces/ITransformData.html) | - |

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
| `data` | [`ITransformData`](./../interfaces/ITransformData.html) |
| `preData` | [`ITransformData`](./../interfaces/ITransformData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number` = `100`

自定义组件的更新优先级。

#### [#](#Overrides) Overrides

[Component](./Component.html).[priority](./Component.html#priority)

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html)

详见[TransformSchema](./../modules.html#TransformSchema)。

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

### [#](#layer) layer

• `get` **layer**(): `number`

#### [#](#Returns-7) Returns

`number`

• `set` **layer**(`value`): `void`

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `value` | `number` |

#### [#](#Returns-8) Returns

`void`

---

### [#](#node) node

• `get` **node**(): `default`

#### [#](#Returns-9) Returns

`default`

---

### [#](#position) position

• `get` **position**(): [`Vector3`](./Vector3.html)

#### [#](#Returns-10) Returns

[`Vector3`](./Vector3.html)

---

### [#](#quaternion) quaternion

• `get` **quaternion**(): [`Quaternion`](./Quaternion.html)

#### [#](#Returns-11) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#rotation) rotation

• `get` **rotation**(): [`Vector3`](./Vector3.html)

注意如果这里直接修改，使用**弧度**。

#### [#](#Returns-12) Returns

[`Vector3`](./Vector3.html)

---

### [#](#scale) scale

• `get` **scale**(): [`Vector3`](./Vector3.html)

#### [#](#Returns-13) Returns

[`Vector3`](./Vector3.html)

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-14) Returns

[`Scene`](./Scene.html)

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-15) Returns

`number`

---

### [#](#visible) visible

• `get` **visible**(): `boolean`

#### [#](#Returns-16) Returns

`boolean`

• `set` **visible**(`value`): `void`

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `value` | `boolean` |

#### [#](#Returns-17) Returns

`void`

---

### [#](#worldForward) worldForward

• `get` **worldForward**(): [`Vector3`](./Vector3.html)

获取世界前向向量，**注意不可修改**。

#### [#](#Returns-18) Returns

[`Vector3`](./Vector3.html)

---

### [#](#worldMatrix) worldMatrix

• `get` **worldMatrix**(): [`Matrix4`](./Matrix4.html)

获取世界矩阵，**注意不可修改**。

#### [#](#Returns-19) Returns

[`Matrix4`](./Matrix4.html)

---

### [#](#worldPosition) worldPosition

• `get` **worldPosition**(): [`Vector3`](./Vector3.html)

获取世界绝对位移，**注意不可修改**。

#### [#](#Returns-20) Returns

[`Vector3`](./Vector3.html)

---

### [#](#worldQuaternion) worldQuaternion

• `get` **worldQuaternion**(): [`Quaternion`](./Quaternion.html)

获取世界绝对旋转，**注意不可修改**。

#### [#](#Returns-21) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#worldRight) worldRight

• `get` **worldRight**(): [`Vector3`](./Vector3.html)

获取世界右向向量，**注意不可修改**。

#### [#](#Returns-22) Returns

[`Vector3`](./Vector3.html)

---

### [#](#worldScale) worldScale

• `get` **worldScale**(): [`Vector3`](./Vector3.html)

获取世界绝对缩放，**注意不可修改**。

#### [#](#Returns-23) Returns

[`Vector3`](./Vector3.html)

---

### [#](#worldUp) worldUp

• `get` **worldUp**(): [`Vector3`](./Vector3.html)

获取世界上向向量，**注意不可修改**。

#### [#](#Returns-24) Returns

[`Vector3`](./Vector3.html)

## [#](#Methods-2) Methods

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`ITransformData`](./../interfaces/ITransformData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`ITransformData`](./../interfaces/ITransformData.html) |

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-25) Returns

[`ITransformData`](./../interfaces/ITransformData.html)[`T`]

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`ITransformData`](./../interfaces/ITransformData.html)> |

#### [#](#Returns-26) Returns

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
| `T` | extends keyof [`ITransformData`](./../interfaces/ITransformData.html) |

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`ITransformData`](./../interfaces/ITransformData.html)[`T`] |

#### [#](#Returns-27) Returns

`void`

#### [#](#Inherited-from-10) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

---

### [#](#setLocalMatrix) setLocalMatrix

▸ **setLocalMatrix**(`mat`): `void`

直接设置本地矩阵。

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `mat` | [`Matrix4`](./Matrix4.html) |

#### [#](#Returns-28) Returns

`void`

Incorrect translation.