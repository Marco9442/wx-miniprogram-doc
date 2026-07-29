[xr-frame](./../) / [Exports](./../modules.html) / PhysicsSystem

# [#](#Class-PhysicsSystem) Class: PhysicsSystem

物理系统，管理着场景中的所有[轮廓](./Shape.html)和[刚体](./Rigidbody.html)。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IPhysicsSystemData`](./../interfaces/IPhysicsSystemData.html)>

  ↳ **`PhysicsSystem`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./PhysicsSystem.html#constructor)

### [#](#Events) Events

- [onAdd](./PhysicsSystem.html#onAdd)
- [onRelease](./PhysicsSystem.html#onRelease)
- [onRemove](./PhysicsSystem.html#onRemove)
- [onTick](./PhysicsSystem.html#onTick)
- [onUpdate](./PhysicsSystem.html#onUpdate)

### [#](#Properties) Properties

- [enableSimulation](./PhysicsSystem.html#enableSimulation)
- [fixedDeltaTime](./PhysicsSystem.html#fixedDeltaTime)
- [maxPhysicsDeltaTime](./PhysicsSystem.html#maxPhysicsDeltaTime)
- [priority](./PhysicsSystem.html#priority)
- [schema](./PhysicsSystem.html#schema)
- [EVENTS](./PhysicsSystem.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./PhysicsSystem.html#el)
- [gravity](./PhysicsSystem.html#gravity)
- [scene](./PhysicsSystem.html#scene)
- [version](./PhysicsSystem.html#version)

### [#](#Methods) Methods

- [getData](./PhysicsSystem.html#getData)
- [ignoreLayerCollision](./PhysicsSystem.html#ignoreLayerCollision)
- [raycast](./PhysicsSystem.html#raycast)
- [setData](./PhysicsSystem.html#setData)
- [setDataOne](./PhysicsSystem.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new PhysicsSystem**()

#### [#](#Overrides) Overrides

[Component](./Component.html).[constructor](./Component.html#constructor)

## [#](#Events-2) Events

### [#](#onAdd) onAdd

▸ **onAdd**(): `void`

所挂载的`element`被挂载到场景时触发的回调。

#### [#](#Returns) Returns

`void`

#### [#](#Inherited-from) Inherited from

[Component](./Component.html).[onAdd](./Component.html#onAdd)

---

### [#](#onRelease) onRelease

▸ **onRelease**(`data`): `void`

从被挂载的`element`上被移除，或是`element`被销毁时，触发的回调。
一般用于释放持有的资源。

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IPhysicsSystemData`](./../interfaces/IPhysicsSystemData.html) |

#### [#](#Returns-2) Returns

`void`

#### [#](#Inherited-from-2) Inherited from

[Component](./Component.html).[onRelease](./Component.html#onRelease)

---

### [#](#onRemove) onRemove

▸ **onRemove**(`parent`, `data`): `void`

所挂载的`element`从父节点`parent`被移除时，或者自己从`element`上被移除时，触发的回调。
一般用于消除功能的运作。
**如果一个组件的元素直接被销毁了，那这个组件就不会经历onRemove而是直接进入onRelease。**

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `parent` | [`Element`](./Element.html) |
| `data` | [`IPhysicsSystemData`](./../interfaces/IPhysicsSystemData.html) |

#### [#](#Returns-3) Returns

`void`

#### [#](#Inherited-from-3) Inherited from

[Component](./Component.html).[onRemove](./Component.html#onRemove)

---

### [#](#onTick) onTick

• **onTick**:

#### [#](#Inherited-from-4) Inherited from

[Component](./Component.html).[onTick](./Component.html#onTick)

---

### [#](#onUpdate) onUpdate

▸ **onUpdate**(`data`, `preData`): `void`

数据更新时触发的回调。

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IPhysicsSystemData`](./../interfaces/IPhysicsSystemData.html) |
| `preData` | [`IPhysicsSystemData`](./../interfaces/IPhysicsSystemData.html) |

#### [#](#Returns-4) Returns

`void`

#### [#](#Inherited-from-5) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#enableSimulation) enableSimulation

• **enableSimulation**: `boolean` = `false`

是否进行物理模拟。

---

### [#](#fixedDeltaTime) fixedDeltaTime

• **fixedDeltaTime**: `number` = `0.02`

---

### [#](#maxPhysicsDeltaTime) maxPhysicsDeltaTime

• **maxPhysicsDeltaTime**: `number` = `0.1`

---

### [#](#priority) priority

• `Readonly` **priority**: `number`

自定义组件的更新优先级。

#### [#](#Inherited-from-6) Inherited from

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

#### [#](#Returns-5) Returns

[`Element`](./Element.html)

---

### [#](#gravity) gravity

• `get` **gravity**(): [`Vector3`](./Vector3.html)

全局重力。

**`default`** [0, -9.8, 0]

#### [#](#Returns-6) Returns

[`Vector3`](./Vector3.html)

• `set` **gravity**(`v`): `void`

全局重力。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `v` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-7) Returns

`void`

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

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IPhysicsSystemData`](./../interfaces/IPhysicsSystemData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends `never` |

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-10) Returns

[`IPhysicsSystemData`](./../interfaces/IPhysicsSystemData.html)[`T`]

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#ignoreLayerCollision) ignoreLayerCollision

▸ **ignoreLayerCollision**(`layer1`, `layer2`, `ignore?`): `void`

设定某一对layer之间是否会发生碰撞。

#### [#](#Parameters-6) Parameters

| Name | Type | Default value | Description |
| --- | --- | --- | --- |
| `layer1` | `number` | `undefined` | - |
| `layer2` | `number` | `undefined` | - |
| `ignore` | `boolean` | `true` | `true`表示**不**碰撞。 |

#### [#](#Returns-11) Returns

`void`

---

### [#](#raycast) raycast

▸ **raycast**(`desc`): `boolean`

射线检测，判断给定射线是否与至少一个轮廓相交，并返回与**最近**的那个轮廓相交的信息。
返回的信息记录在desc.hit里，需要事先创建一个RaycastHit对象来负责接收。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `desc` | [`RaycastDesc`](./../modules.html#RaycastDesc) |

#### [#](#Returns-12) Returns

`boolean`

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IPhysicsSystemData`](./../interfaces/IPhysicsSystemData.html)> |

#### [#](#Returns-13) Returns

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
| `T` | extends `never` |

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IPhysicsSystemData`](./../interfaces/IPhysicsSystemData.html)[`T`] |

#### [#](#Returns-14) Returns

`void`

#### [#](#Inherited-from-11) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.