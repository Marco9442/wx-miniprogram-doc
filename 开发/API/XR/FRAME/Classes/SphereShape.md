XR-FRAME/Classes/SphereShape/
[xr-frame](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/) / [Exports](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/modules.html) / SphereShape
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Class-SphereShape) Class: SphereShape
为当前元素创建一个可交互的球状轮廓。
可通过在标签上添加`sphere-shape`属性来为元素添加该组件。
\*\*`see`\*\* [ISphereShapeData](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Hierarchy) Hierarchy
- [`Shape`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html) < [`ISphereShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html) >
↳ \*\*`SphereShape`\*\*
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Table-of-contents) Table of contents
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Constructors) Constructors
- [constructor](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#constructor)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Events) Events
- [onAdd](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#onAdd)
- [onRelease](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#onRelease)
- [onRemove](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#onRemove)
- [onTick](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#onTick)
- [onUpdate](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#onUpdate)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Properties) Properties
- [implType](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#implType)
- [priority](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#priority)
- [schema](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#schema)
- [shadowRoot](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#shadowRoot)
- [EVENTS](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#EVENTS)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Accessors) Accessors
- [el](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#el)
- [scene](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#scene)
- [type](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#type)
- [version](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#version)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Methods) Methods
- [getBasicImpl](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#getBasicImpl)
- [getData](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#getData)
- [getGLTFRootShape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#getGLTFRootShape)
- [getShadowShapes](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#getShadowShapes)
- [initDelegates](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#initDelegates)
- [resetListeners](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#resetListeners)
- [setAsShadow](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#setAsShadow)
- [setData](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#setData)
- [setDataOne](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html#setDataOne)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Constructors-2) Constructors
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#constructor) constructor
• \*\*new SphereShape\*\*()
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [constructor](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#constructor)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Events-2) Events
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#onAdd) onAdd
▸ \*\*onAdd\*\*(`parent`, `data`): `void`
所挂载的`element`被挂载到场景时触发的回调。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Parameters) Parameters
| Name | Type |
| --- | --- |
| `parent` | [`Element`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Element.html) |
| `data` | [`ISphereShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html) |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns) Returns
`void`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-2) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [onAdd](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#onAdd)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#onRelease) onRelease
▸ \*\*onRelease\*\*(`data`): `void`
从被挂载的`element`上被移除，或是`element`被销毁时，触发的回调。
一般用于释放持有的资源。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Parameters-2) Parameters
| Name | Type |
| --- | --- |
| `data` | [`IShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeData.html) |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-2) Returns
`void`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-3) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [onRelease](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#onRelease)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#onRemove) onRemove
▸ \*\*onRemove\*\*(`parent`, `data`): `void`
所挂载的`element`从父节点`parent`被移除时，或者自己从`element`上被移除时，触发的回调。
一般用于消除功能的运作。
\*\*如果一个组件的元素直接被销毁了，那这个组件就不会经历onRemove而是直接进入onRelease。\*\*
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Parameters-3) Parameters
| Name | Type |
| --- | --- |
| `parent` | [`Element`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Element.html) |
| `data` | [`IShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeData.html) |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-3) Returns
`void`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-4) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [onRemove](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#onRemove)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#onTick) onTick
▸ \*\*onTick\*\*(`dateTime`, `data`): `void`
渲染每帧触发的回调。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Parameters-4) Parameters
| Name | Type |
| --- | --- |
| `dateTime` | `number` |
| `data` | [`ISphereShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html) |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-4) Returns
`void`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-5) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [onTick](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#onTick)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#onUpdate) onUpdate
▸ \*\*onUpdate\*\*(`data`, `preData`): `void`
数据更新时触发的回调。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Parameters-5) Parameters
| Name | Type |
| --- | --- |
| `data` | [`ISphereShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html) |
| `preData` | [`ISphereShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html) |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-5) Returns
`void`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-6) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [onUpdate](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#onUpdate)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Properties-2) Properties
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#implType) implType
• \*\*implType\*\*: `ShapeImplType`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-7) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [implType](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#implType)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#priority) priority
• `Readonly` \*\*priority\*\*: `number` = `400`
自定义组件的更新优先级。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-8) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [priority](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#priority)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#schema) schema
• `Readonly` \*\*schema\*\*: [`IComponentSchema`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IComponentSchema.html)
自定义组件的`schema`。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Overrides) Overrides
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [schema](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#schema)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#shadowRoot) shadowRoot
• `Optional` \*\*shadowRoot\*\*: `GLTFAbstractShape`< [`ISphereShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html) >
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-9) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [shadowRoot](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#shadowRoot)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#EVENTS) EVENTS
▪ `Static` \*\*EVENTS\*\*: `string`\[\]
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Overrides-2) Overrides
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [EVENTS](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#EVENTS)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Accessors-2) Accessors
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#el) el
• `get` \*\*el\*\*(): [`Element`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Element.html)
挂载的元素。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-6) Returns
[`Element`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Element.html)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#scene) scene
• `get` \*\*scene\*\*(): [`Scene`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Scene.html)
当前场景。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-7) Returns
[`Scene`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Scene.html)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#type) type
• `get` \*\*type\*\*(): [`EShapeType`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/enums/EShapeType.html)
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-8) Returns
[`EShapeType`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/enums/EShapeType.html)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#version) version
• `get` \*\*version\*\*(): `number`
当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-9) Returns
`number`
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Methods-2) Methods
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#getBasicImpl) getBasicImpl
▸ \*\*getBasicImpl\*\*(): `BasicShape`< [`ISphereShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html) >
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-10) Returns
`BasicShape`< [`ISphereShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html) >
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-10) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [getBasicImpl](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#getBasicImpl)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#getData) getData
▸ \*\*getData\*\* <`T`>(`key`): [`IShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeData.html)\[`T`\]
获取一个当前值。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Type-parameters) Type parameters
| Name | Type |
| --- | --- |
| `T` | extends keyof [`IShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeData.html) |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Parameters-6) Parameters
| Name | Type |
| --- | --- |
| `key` | `T` |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-11) Returns
[`IShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeData.html)\[`T`\]
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-11) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [getData](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#getData)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#getGLTFRootShape) getGLTFRootShape
▸ \*\*getGLTFRootShape\*\*(): [`Shape`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html) < [`ISphereShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html) >
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-12) Returns
[`Shape`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html) < [`ISphereShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html) >
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-12) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [getGLTFRootShape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#getGLTFRootShape)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#getShadowShapes) getShadowShapes
▸ \*\*getShadowShapes\*\*(): [`Shape`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html) < [`ISphereShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html) >\[\]
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-13) Returns
[`Shape`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html) < [`ISphereShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html) >\[\]
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-13) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [getShadowShapes](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#getShadowShapes)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#initDelegates) initDelegates
▸ \*\*initDelegates\*\*(`el`): `void`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Parameters-7) Parameters
| Name | Type |
| --- | --- |
| `el` | [`Element`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Element.html) |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-14) Returns
`void`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-14) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [initDelegates](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#initDelegates)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#resetListeners) resetListeners
▸ \*\*resetListeners\*\*(): `void`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-15) Returns
`void`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-15) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [resetListeners](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#resetListeners)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#setAsShadow) setAsShadow
▸ \*\*setAsShadow\*\*(`root`, `transform`): `void`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Parameters-8) Parameters
| Name | Type |
| --- | --- |
| `root` | `GLTFAbstractShape`< [`ISphereShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ISphereShapeData.html) > |
| `transform` | `TQS` |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-16) Returns
`void`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-16) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [setAsShadow](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#setAsShadow)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#setData) setData
▸ \*\*setData\*\*(`data`): `void`
不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Parameters-9) Parameters
| Name | Type |
| --- | --- |
| `data` | `Partial`< [`IShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeData.html) > |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-17) Returns
`void`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-17) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [setData](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#setData)
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#setDataOne) setDataOne
▸ \*\*setDataOne\*\* <`T`>(`key`, `value`): `void`
设置一个数据。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Type-parameters-2) Type parameters
| Name | Type |
| --- | --- |
| `T` | extends keyof [`IShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeData.html) |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Parameters-10) Parameters
| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IShapeData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IShapeData.html)\[`T`\] |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Returns-18) Returns
`void`
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/SphereShape.html\#Inherited-from-18) Inherited from
[Shape](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html). [setDataOne](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Shape.html#setDataOne)