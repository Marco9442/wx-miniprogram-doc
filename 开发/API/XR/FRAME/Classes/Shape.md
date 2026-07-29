[xr-frame](./../) / [Exports](./../modules.html) / Shape

# [#](#Class-Shape-T) Class: Shape<T>

轮廓组件的基类。
为元素添加*该组件的子类*可以创建一个可用于交互的轮廓。

> 💡 只要创建了轮廓，在点击该物体时就可以触发事件：
>
> - touch-shape: 点击物体事件，回调参数为[IShapeTouchEvent](./../interfaces/IShapeTouchEvent.html)；
> - drag-shape: 拖拽物体事件，回调参数为[IShapeDragEvent](./../interfaces/IShapeDragEvent.html)；
> - untouch-shape: 松开物体事件，回调参数为[IShapeTouchEvent](./../interfaces/IShapeTouchEvent.html)；
>
> 绑定事件的方法可参考以下代码：
>
> `<xr-node sphere-shape bind:touch-shape="handleTouchShape"></xr-node>`

> 💡 如果想要将轮廓可视化来确认轮廓大小，可以在同一个元素下添加[ShapeGizmos](./ShapeGizmos.html)组件，或在标签上添加`shape-gizmo`属性（对MeshShape不起作用）。

**`abstract`**

## [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`IShapeData`](./../interfaces/IShapeData.html) = `any` |

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IShapeData`](./../interfaces/IShapeData.html)>

  ↳ **`Shape`**

  ↳↳ [`SphereShape`](./SphereShape.html)

  ↳↳ [`MeshShape`](./MeshShape.html)

  ↳↳ [`CapsuleShape`](./CapsuleShape.html)

  ↳↳ [`CubeShape`](./CubeShape.html)

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Shape.html#constructor)

### [#](#Events) Events

- [onAdd](./Shape.html#onAdd)
- [onRelease](./Shape.html#onRelease)
- [onRemove](./Shape.html#onRemove)
- [onTick](./Shape.html#onTick)
- [onUpdate](./Shape.html#onUpdate)

### [#](#Properties) Properties

- [implType](./Shape.html#implType)
- [priority](./Shape.html#priority)
- [schema](./Shape.html#schema)
- [shadowRoot](./Shape.html#shadowRoot)
- [EVENTS](./Shape.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./Shape.html#el)
- [scene](./Shape.html#scene)
- [type](./Shape.html#type)
- [version](./Shape.html#version)

### [#](#Methods) Methods

- [getBasicImpl](./Shape.html#getBasicImpl)
- [getData](./Shape.html#getData)
- [getGLTFRootShape](./Shape.html#getGLTFRootShape)
- [getShadowShapes](./Shape.html#getShadowShapes)
- [initDelegates](./Shape.html#initDelegates)
- [resetListeners](./Shape.html#resetListeners)
- [setAsShadow](./Shape.html#setAsShadow)
- [setData](./Shape.html#setData)
- [setDataOne](./Shape.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Shape**<`T`>()

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`IShapeData`](./../interfaces/IShapeData.html) = `any` |

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
| `data` | `T` |

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
| `data` | [`IShapeData`](./../interfaces/IShapeData.html) |

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
| `data` | [`IShapeData`](./../interfaces/IShapeData.html) |

#### [#](#Returns-3) Returns

`void`

#### [#](#Inherited-from-4) Inherited from

[Component](./Component.html).[onRemove](./Component.html#onRemove)

---

### [#](#onTick) onTick

▸ **onTick**(`dateTime`, `data`): `void`

渲染每帧触发的回调。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `dateTime` | `number` |
| `data` | `T` |

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
| `data` | `T` |
| `preData` | `T` |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#implType) implType

• **implType**: `ShapeImplType`

---

### [#](#priority) priority

• `Readonly` **priority**: `number` = `400`

自定义组件的更新优先级。

#### [#](#Overrides) Overrides

[Component](./Component.html).[priority](./Component.html#priority)

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html) = `{}`

自定义组件的`schema`。

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#shadowRoot) shadowRoot

• `Optional` **shadowRoot**: `GLTFAbstractShape`<`T`>

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

▸ **getBasicImpl**(): `BasicShape`<`T`>

#### [#](#Returns-10) Returns

`BasicShape`<`T`>

---

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IShapeData`](./../interfaces/IShapeData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters-3) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IShapeData`](./../interfaces/IShapeData.html) |

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-11) Returns

[`IShapeData`](./../interfaces/IShapeData.html)[`T`]

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#getGLTFRootShape) getGLTFRootShape

▸ **getGLTFRootShape**(): [`Shape`](./Shape.html)<`T`>

#### [#](#Returns-12) Returns

[`Shape`](./Shape.html)<`T`>

---

### [#](#getShadowShapes) getShadowShapes

▸ **getShadowShapes**(): [`Shape`](./Shape.html)<`T`>[]

#### [#](#Returns-13) Returns

[`Shape`](./Shape.html)<`T`>[]

---

### [#](#initDelegates) initDelegates

▸ **initDelegates**(`el`): `void`

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `el` | [`Element`](./Element.html) |

#### [#](#Returns-14) Returns

`void`

---

### [#](#resetListeners) resetListeners

▸ **resetListeners**(): `void`

#### [#](#Returns-15) Returns

`void`

---

### [#](#setAsShadow) setAsShadow

▸ **setAsShadow**(`root`, `transform`): `void`

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `root` | `GLTFAbstractShape`<`T`> |
| `transform` | `TQS` |

#### [#](#Returns-16) Returns

`void`

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

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[setData](./Component.html#setData)

---

### [#](#setDataOne) setDataOne

▸ **setDataOne**<`T`>(`key`, `value`): `void`

设置一个数据。

#### [#](#Type-parameters-4) Type parameters

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

#### [#](#Inherited-from-10) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.