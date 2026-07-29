[xr-frame](./../) / [Exports](./../modules.html) / ShapeInteract

# [#](#Class-ShapeInteract) Class: ShapeInteract

拥有ShapeInterace组件的Shape才能与其他Shape发生交互。
将`collide`属性设置为true来与其他Shape进行物理碰撞，仅当两个Shape的collide属性**都为true**时它们才能发生碰撞。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IShapeInteractData`](./../interfaces/IShapeInteractData.html)>

  ↳ **`ShapeInteract`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./ShapeInteract.html#constructor)

### [#](#Events) Events

- [onAdd](./ShapeInteract.html#onAdd)
- [onRelease](./ShapeInteract.html#onRelease)
- [onRemove](./ShapeInteract.html#onRemove)
- [onTick](./ShapeInteract.html#onTick)
- [onUpdate](./ShapeInteract.html#onUpdate)

### [#](#Properties) Properties

- [priority](./ShapeInteract.html#priority)
- [schema](./ShapeInteract.html#schema)
- [EVENTS](./ShapeInteract.html#EVENTS)

### [#](#Accessors) Accessors

- [bounceCombine](./ShapeInteract.html#bounceCombine)
- [bounciness](./ShapeInteract.html#bounciness)
- [dynamicFriction](./ShapeInteract.html#dynamicFriction)
- [el](./ShapeInteract.html#el)
- [frictionCombine](./ShapeInteract.html#frictionCombine)
- [scene](./ShapeInteract.html#scene)
- [staticFriction](./ShapeInteract.html#staticFriction)
- [version](./ShapeInteract.html#version)

### [#](#Methods) Methods

- [getData](./ShapeInteract.html#getData)
- [getInteractType](./ShapeInteract.html#getInteractType)
- [setData](./ShapeInteract.html#setData)
- [setDataOne](./ShapeInteract.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new ShapeInteract**()

#### [#](#Overrides) Overrides

[Component](./Component.html).[constructor](./Component.html#constructor)

## [#](#Events-2) Events

### [#](#onAdd) onAdd

▸ **onAdd**(`parent`, `data`): `void`

所挂载的`element`被挂载到场景时触发的回调。

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `parent` | [`Element`](./Element.html) |
| `data` | [`IShapeInteractData`](./../interfaces/IShapeInteractData.html) |

#### [#](#Returns) Returns

`void`

#### [#](#Inherited-from) Inherited from

[Component](./Component.html).[onAdd](./Component.html#onAdd)

---

### [#](#onRelease) onRelease

▸ **onRelease**(`data`): `void`

从被挂载的`element`上被移除，或是`element`被销毁时，触发的回调。
一般用于释放持有的资源。

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IShapeInteractData`](./../interfaces/IShapeInteractData.html) |

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

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `parent` | [`Element`](./Element.html) |
| `data` | [`IShapeInteractData`](./../interfaces/IShapeInteractData.html) |

#### [#](#Returns-3) Returns

`void`

#### [#](#Inherited-from-3) Inherited from

[Component](./Component.html).[onRemove](./Component.html#onRemove)

---

### [#](#onTick) onTick

▸ **onTick**(`deltaTime`, `data`): `void`

渲染每帧触发的回调。

#### [#](#Parameters-4) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `deltaTime` | `number` | 单位为毫秒(ms)。 |
| `data` | [`IShapeInteractData`](./../interfaces/IShapeInteractData.html) | - |

#### [#](#Returns-4) Returns

`void`

#### [#](#Inherited-from-4) Inherited from

[Component](./Component.html).[onTick](./Component.html#onTick)

---

### [#](#onUpdate) onUpdate

▸ **onUpdate**(`data`, `preData`): `void`

数据更新时触发的回调。

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IShapeInteractData`](./../interfaces/IShapeInteractData.html) |
| `preData` | [`IShapeInteractData`](./../interfaces/IShapeInteractData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-5) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number`

自定义组件的更新优先级。

#### [#](#Inherited-from-6) Inherited from

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

## [#](#Accessors-2) Accessors

### [#](#bounceCombine) bounceCombine

• `get` **bounceCombine**(): `CombineMode`

如何结合发生碰撞的两个物体的弹性系数。

**`default`** {@link CombineMode.Average}

#### [#](#Returns-6) Returns

`CombineMode`

• `set` **bounceCombine**(`v`): `void`

如何结合发生碰撞的两个物体的弹性系数。

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `v` | `CombineMode` |

#### [#](#Returns-7) Returns

`void`

---

### [#](#bounciness) bounciness

• `get` **bounciness**(): `number`

弹性系数，决定碰撞时的能量损失比例。

弹性系数 = 1时，碰撞无能量损失。

**`limit`** 0 <= bounciness <= 1

**`default`** 0

#### [#](#Returns-8) Returns

`number`

• `set` **bounciness**(): `void`

弹性系数，决定碰撞时的能量损失比例。

弹性系数 = 1时，碰撞无能量损失。

#### [#](#Returns-9) Returns

`void`

---

### [#](#dynamicFriction) dynamicFriction

• `get` **dynamicFriction**(): `number`

动摩擦系数。

**`limit`** 0 <= dynamicFriction <= 1

**`default`** 0.6

#### [#](#Returns-10) Returns

`number`

• `set` **dynamicFriction**(): `void`

动摩擦系数。

#### [#](#Returns-11) Returns

`void`

---

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-12) Returns

[`Element`](./Element.html)

---

### [#](#frictionCombine) frictionCombine

• `get` **frictionCombine**(): `CombineMode`

如何结合发生碰撞的两个物体的摩擦系数。

**`default`** {@link CombineMode.Average}

#### [#](#Returns-13) Returns

`CombineMode`

• `set` **frictionCombine**(`v`): `void`

如何结合发生碰撞的两个物体的摩擦系数。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `v` | `CombineMode` |

#### [#](#Returns-14) Returns

`void`

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-15) Returns

[`Scene`](./Scene.html)

---

### [#](#staticFriction) staticFriction

• `get` **staticFriction**(): `number`

静摩擦系数

**`limit`** 0 <= staticFriction <= 1

**`default`** 0.6

#### [#](#Returns-16) Returns

`number`

• `set` **staticFriction**(): `void`

静摩擦系数

#### [#](#Returns-17) Returns

`void`

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-18) Returns

`number`

## [#](#Methods-2) Methods

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IShapeInteractData`](./../interfaces/IShapeInteractData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IShapeInteractData`](./../interfaces/IShapeInteractData.html) |

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-19) Returns

[`IShapeInteractData`](./../interfaces/IShapeInteractData.html)[`T`]

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#getInteractType) getInteractType

▸ **getInteractType**(): `EShapeInteractType`

#### [#](#Returns-20) Returns

`EShapeInteractType`

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IShapeInteractData`](./../interfaces/IShapeInteractData.html)> |

#### [#](#Returns-21) Returns

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
| `T` | extends keyof [`IShapeInteractData`](./../interfaces/IShapeInteractData.html) |

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IShapeInteractData`](./../interfaces/IShapeInteractData.html)[`T`] |

#### [#](#Returns-22) Returns

`void`

#### [#](#Inherited-from-10) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.