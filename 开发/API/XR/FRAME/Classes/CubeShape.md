[xr-frame](./../) / [Exports](./../modules.html) / CubeShape

# [#](#Class-CubeShape) Class: CubeShape

为当前元素创建一个可交互的长方体轮廓。
可通过在标签上添加`cube-shape`属性来为元素添加该组件。

**`see`** [ICubeShapeData](./../interfaces/ICubeShapeData.html)

## [#](#Hierarchy) Hierarchy

- [`Shape`](./Shape.html)<[`ICubeShapeData`](./../interfaces/ICubeShapeData.html)>

  ↳ **`CubeShape`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./CubeShape.html#constructor)

### [#](#Events) Events

- [onAdd](./CubeShape.html#onAdd)
- [onRelease](./CubeShape.html#onRelease)
- [onRemove](./CubeShape.html#onRemove)
- [onTick](./CubeShape.html#onTick)
- [onUpdate](./CubeShape.html#onUpdate)

### [#](#Properties) Properties

- [implType](./CubeShape.html#implType)
- [priority](./CubeShape.html#priority)
- [schema](./CubeShape.html#schema)
- [shadowRoot](./CubeShape.html#shadowRoot)
- [EVENTS](./CubeShape.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./CubeShape.html#el)
- [scene](./CubeShape.html#scene)
- [type](./CubeShape.html#type)
- [version](./CubeShape.html#version)

### [#](#Methods) Methods

- [getBasicImpl](./CubeShape.html#getBasicImpl)
- [getData](./CubeShape.html#getData)
- [getGLTFRootShape](./CubeShape.html#getGLTFRootShape)
- [getShadowShapes](./CubeShape.html#getShadowShapes)
- [initDelegates](./CubeShape.html#initDelegates)
- [resetListeners](./CubeShape.html#resetListeners)
- [setAsShadow](./CubeShape.html#setAsShadow)
- [setData](./CubeShape.html#setData)
- [setDataOne](./CubeShape.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new CubeShape**()

#### [#](#Inherited-from) Inherited from

[Shape](./Shape.html).[constructor](./Shape.html#constructor)

## [#](#Events-2) Events

### [#](#onAdd) onAdd

▸ **onAdd**(`parent`, `data`): `void`

所挂载的`element`被挂载到场景时触发的回调。

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `parent` | [`Element`](./Element.html) |
| `data` | [`ICubeShapeData`](./../interfaces/ICubeShapeData.html) |

#### [#](#Returns) Returns

`void`

#### [#](#Inherited-from-2) Inherited from

[Shape](./Shape.html).[onAdd](./Shape.html#onAdd)

---

### [#](#onRelease) onRelease

▸ **onRelease**(`data`): `void`

从被挂载的`element`上被移除，或是`element`被销毁时，触发的回调。
一般用于释放持有的资源。

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IShapeData`](./../interfaces/IShapeData.html) |

#### [#](#Returns-2) Returns

`void`

#### [#](#Inherited-from-3) Inherited from

[Shape](./Shape.html).[onRelease](./Shape.html#onRelease)

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
| `data` | [`IShapeData`](./../interfaces/IShapeData.html) |

#### [#](#Returns-3) Returns

`void`

#### [#](#Inherited-from-4) Inherited from

[Shape](./Shape.html).[onRemove](./Shape.html#onRemove)

---

### [#](#onTick) onTick

▸ **onTick**(`dateTime`, `data`): `void`

渲染每帧触发的回调。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `dateTime` | `number` |
| `data` | [`ICubeShapeData`](./../interfaces/ICubeShapeData.html) |

#### [#](#Returns-4) Returns

`void`

#### [#](#Inherited-from-5) Inherited from

[Shape](./Shape.html).[onTick](./Shape.html#onTick)

---

### [#](#onUpdate) onUpdate

▸ **onUpdate**(`data`, `preData`): `void`

数据更新时触发的回调。

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `data` | [`ICubeShapeData`](./../interfaces/ICubeShapeData.html) |
| `preData` | [`ICubeShapeData`](./../interfaces/ICubeShapeData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Shape](./Shape.html).[onUpdate](./Shape.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#implType) implType

• **implType**: `ShapeImplType`

#### [#](#Inherited-from-7) Inherited from

[Shape](./Shape.html).[implType](./Shape.html#implType)

---

### [#](#priority) priority

• `Readonly` **priority**: `number` = `400`

自定义组件的更新优先级。

#### [#](#Inherited-from-8) Inherited from

[Shape](./Shape.html).[priority](./Shape.html#priority)

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html)

自定义组件的`schema`。

#### [#](#Overrides) Overrides

[Shape](./Shape.html).[schema](./Shape.html#schema)

---

### [#](#shadowRoot) shadowRoot

• `Optional` **shadowRoot**: `GLTFAbstractShape`<[`ICubeShapeData`](./../interfaces/ICubeShapeData.html)>

#### [#](#Inherited-from-9) Inherited from

[Shape](./Shape.html).[shadowRoot](./Shape.html#shadowRoot)

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[]

#### [#](#Overrides-2) Overrides

[Shape](./Shape.html).[EVENTS](./Shape.html#EVENTS)

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

### [#](#type) type

• `get` **type**(): [`EShapeType`](./../enums/EShapeType.html)

#### [#](#Returns-8) Returns

[`EShapeType`](./../enums/EShapeType.html)

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-9) Returns

`number`

## [#](#Methods-2) Methods

### [#](#getBasicImpl) getBasicImpl

▸ **getBasicImpl**(): `BasicShape`<[`ICubeShapeData`](./../interfaces/ICubeShapeData.html)>

#### [#](#Returns-10) Returns

`BasicShape`<[`ICubeShapeData`](./../interfaces/ICubeShapeData.html)>

#### [#](#Inherited-from-10) Inherited from

[Shape](./Shape.html).[getBasicImpl](./Shape.html#getBasicImpl)

---

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IShapeData`](./../interfaces/IShapeData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IShapeData`](./../interfaces/IShapeData.html) |

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-11) Returns

[`IShapeData`](./../interfaces/IShapeData.html)[`T`]

#### [#](#Inherited-from-11) Inherited from

[Shape](./Shape.html).[getData](./Shape.html#getData)

---

### [#](#getGLTFRootShape) getGLTFRootShape

▸ **getGLTFRootShape**(): [`Shape`](./Shape.html)<[`ICubeShapeData`](./../interfaces/ICubeShapeData.html)>

#### [#](#Returns-12) Returns

[`Shape`](./Shape.html)<[`ICubeShapeData`](./../interfaces/ICubeShapeData.html)>

#### [#](#Inherited-from-12) Inherited from

[Shape](./Shape.html).[getGLTFRootShape](./Shape.html#getGLTFRootShape)

---

### [#](#getShadowShapes) getShadowShapes

▸ **getShadowShapes**(): [`Shape`](./Shape.html)<[`ICubeShapeData`](./../interfaces/ICubeShapeData.html)>[]

#### [#](#Returns-13) Returns

[`Shape`](./Shape.html)<[`ICubeShapeData`](./../interfaces/ICubeShapeData.html)>[]

#### [#](#Inherited-from-13) Inherited from

[Shape](./Shape.html).[getShadowShapes](./Shape.html#getShadowShapes)

---

### [#](#initDelegates) initDelegates

▸ **initDelegates**(`el`): `void`

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `el` | [`Element`](./Element.html) |

#### [#](#Returns-14) Returns

`void`

#### [#](#Inherited-from-14) Inherited from

[Shape](./Shape.html).[initDelegates](./Shape.html#initDelegates)

---

### [#](#resetListeners) resetListeners

▸ **resetListeners**(): `void`

#### [#](#Returns-15) Returns

`void`

#### [#](#Inherited-from-15) Inherited from

[Shape](./Shape.html).[resetListeners](./Shape.html#resetListeners)

---

### [#](#setAsShadow) setAsShadow

▸ **setAsShadow**(`root`, `transform`): `void`

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `root` | `GLTFAbstractShape`<[`ICubeShapeData`](./../interfaces/ICubeShapeData.html)> |
| `transform` | `TQS` |

#### [#](#Returns-16) Returns

`void`

#### [#](#Inherited-from-16) Inherited from

[Shape](./Shape.html).[setAsShadow](./Shape.html#setAsShadow)

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IShapeData`](./../interfaces/IShapeData.html)> |

#### [#](#Returns-17) Returns

`void`

#### [#](#Inherited-from-17) Inherited from

[Shape](./Shape.html).[setData](./Shape.html#setData)

---

### [#](#setDataOne) setDataOne

▸ **setDataOne**<`T`>(`key`, `value`): `void`

设置一个数据。

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IShapeData`](./../interfaces/IShapeData.html) |

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IShapeData`](./../interfaces/IShapeData.html)[`T`] |

#### [#](#Returns-18) Returns

`void`

#### [#](#Inherited-from-18) Inherited from

[Shape](./Shape.html).[setDataOne](./Shape.html#setDataOne)

Incorrect translation.