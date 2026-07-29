[xr-frame](./../) / [Exports](./../modules.html) / Component

# [#](#Class-Component-IData) Class: Component<IData>

组件，系统核心之一。

组件就是`wxml`的标签上写的那些`attribute`，比如`<xr-element transform="position: 1 1 1" />`中，`transform`就是一个组件，`position`是它的一个属性。
这些属性可以在`schema`中被定义，变化时会触发对应的生命周期。
自定义组件最后使用[registerComponent](./../modules.html#registerComponent)，组件的属性可以使用代理规则来简化，比如以上的标签可以简化为`<xr-element position="1 1 1" />`，详见[Element](./Element.html)。

## [#](#Type-parameters) Type parameters

| Name | Description |
| --- | --- |
| `IData` | 组件数据的类型，应当和`schema`中一致，用于TS类型推断。 |

## [#](#Hierarchy) Hierarchy

- **`Component`**

  ↳ [`Transform`](./Transform.html)

  ↳ [`AssetLoad`](./AssetLoad.html)

  ↳ [`Assets`](./Assets.html)

  ↳ [`Camera`](./Camera.html)

  ↳ [`GLTF`](./GLTF.html)

  ↳ [`Light`](./Light.html)

  ↳ [`AssetMaterial`](./AssetMaterial.html)

  ↳ [`Mesh`](./Mesh.html)

  ↳ [`Text`](./Text.html)

  ↳ [`AssetRenderTexture`](./AssetRenderTexture.html)

  ↳ [`Env`](./Env.html)

  ↳ [`Animator`](./Animator.html)

  ↳ [`CameraOrbitControl`](./CameraOrbitControl.html)

  ↳ [`ARTracker`](./ARTracker.html)

  ↳ [`Shape`](./Shape.html)

  ↳ [`Rigidbody`](./Rigidbody.html)

  ↳ [`ShapeInteract`](./ShapeInteract.html)

  ↳ [`ShapeGizmos`](./ShapeGizmos.html)

  ↳ [`AssetPostProcess`](./AssetPostProcess.html)

  ↳ [`AssetsSystem`](./AssetsSystem.html)

  ↳ [`NodeSystem`](./NodeSystem.html)

  ↳ [`TickSystem`](./TickSystem.html)

  ↳ [`AnimationSystem`](./AnimationSystem.html)

  ↳ [`VideoSystem`](./VideoSystem.html)

  ↳ [`RenderSystem`](./RenderSystem.html)

  ↳ [`PhysicsSystem`](./PhysicsSystem.html)

  ↳ [`ARSystem`](./ARSystem.html)

  ↳ [`ShareSystem`](./ShareSystem.html)

  ↳ [`GizmoSystem`](./GizmoSystem.html)

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Component.html#constructor)

### [#](#Events) Events

- [onAdd](./Component.html#onAdd)
- [onRelease](./Component.html#onRelease)
- [onRemove](./Component.html#onRemove)
- [onTick](./Component.html#onTick)
- [onUpdate](./Component.html#onUpdate)

### [#](#Properties) Properties

- [priority](./Component.html#priority)
- [schema](./Component.html#schema)
- [EVENTS](./Component.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./Component.html#el)
- [scene](./Component.html#scene)
- [version](./Component.html#version)

### [#](#Methods) Methods

- [getData](./Component.html#getData)
- [setData](./Component.html#setData)
- [setDataOne](./Component.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Component**<`IData`>()

#### [#](#Type-parameters-2) Type parameters

| Name |
| --- |
| `IData` |

## [#](#Events-2) Events

### [#](#onAdd) onAdd

▸ **onAdd**(`parent`, `data`): `void`

所挂载的`element`被挂载到场景时触发的回调。

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `parent` | [`Element`](./Element.html) |
| `data` | `IData` |

#### [#](#Returns) Returns

`void`

---

### [#](#onRelease) onRelease

▸ **onRelease**(`data`): `void`

从被挂载的`element`上被移除，或是`element`被销毁时，触发的回调。
一般用于释放持有的资源。

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `data` | `IData` |

#### [#](#Returns-2) Returns

`void`

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
| `data` | `IData` |

#### [#](#Returns-3) Returns

`void`

---

### [#](#onTick) onTick

▸ **onTick**(`deltaTime`, `data`): `void`

渲染每帧触发的回调。

#### [#](#Parameters-4) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `deltaTime` | `number` | 单位为毫秒(ms)。 |
| `data` | `IData` | - |

#### [#](#Returns-4) Returns

`void`

---

### [#](#onUpdate) onUpdate

▸ **onUpdate**(`data`, `preData`): `void`

数据更新时触发的回调。

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `data` | `IData` |
| `preData` | `IData` |

#### [#](#Returns-5) Returns

`void`

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number`

自定义组件的更新优先级。

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html) = `{}`

自定义组件的`schema`。

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[] = `[]`

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

▸ **getData**<`T`>(`key`): `IData`[`T`]

获取一个当前值。

#### [#](#Type-parameters-3) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends `string` | `number` | `symbol` |

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-9) Returns

`IData`[`T`]

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<`IData`> |

#### [#](#Returns-10) Returns

`void`

---

### [#](#setDataOne) setDataOne

▸ **setDataOne**<`T`>(`key`, `value`): `void`

设置一个数据。

#### [#](#Type-parameters-4) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends `string` | `number` | `symbol` |

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | `IData`[`T`] |

#### [#](#Returns-11) Returns

`void`

Incorrect translation.