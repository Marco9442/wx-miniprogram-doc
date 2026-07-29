[xr-frame](./../) / [Exports](./../modules.html) / Scene

# [#](#Class-Scene) Class: Scene

场景，系统核心之一。

`Scene`是元素的一种，对应于`xr-scene`标签。
作为整个`xr-frame`组件的根节点，它提供了整个组件运作的一些基本能力，挂在了各大系统，驱动生命周期循环。

## [#](#Hierarchy) Hierarchy

- [`Element`](./Element.html)

  ↳ **`Scene`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Scene.html#constructor)

### [#](#Properties) Properties

- [dataMapping](./Scene.html#dataMapping)
- [defaultComponents](./Scene.html#defaultComponents)
- [isScene](./Scene.html#isScene)
- [TYPE](./Scene.html#TYPE)

### [#](#Accessors) Accessors

- [animation](./Scene.html#animation)
- [ar](./Scene.html#ar)
- [assets](./Scene.html#assets)
- [event](./Scene.html#event)
- [frameHeight](./Scene.html#frameHeight)
- [frameWidth](./Scene.html#frameWidth)
- [gizmo](./Scene.html#gizmo)
- [height](./Scene.html#height)
- [id](./Scene.html#id)
- [inXML](./Scene.html#inXML)
- [name](./Scene.html#name)
- [parent](./Scene.html#parent)
- [physics](./Scene.html#physics)
- [ready](./Scene.html#ready)
- [render](./Scene.html#render)
- [rootShadow](./Scene.html#rootShadow)
- [scene](./Scene.html#scene)
- [share](./Scene.html#share)
- [timestamp](./Scene.html#timestamp)
- [video](./Scene.html#video)
- [width](./Scene.html#width)

### [#](#Methods) Methods

- [addChild](./Scene.html#addChild)
- [addComponent](./Scene.html#addComponent)
- [createEffect](./Scene.html#createEffect)
- [createElement](./Scene.html#createElement)
- [createGeometry](./Scene.html#createGeometry)
- [createImage](./Scene.html#createImage)
- [createMaterial](./Scene.html#createMaterial)
- [createPostProcess](./Scene.html#createPostProcess)
- [createRenderTexture](./Scene.html#createRenderTexture)
- [createTexture](./Scene.html#createTexture)
- [createUniformBlock](./Scene.html#createUniformBlock)
- [createUniformBlockDesc](./Scene.html#createUniformBlockDesc)
- [createVertexLayout](./Scene.html#createVertexLayout)
- [createVideoTexture](./Scene.html#createVideoTexture)
- [dfs](./Scene.html#dfs)
- [getChildAtIndex](./Scene.html#getChildAtIndex)
- [getChildByClass](./Scene.html#getChildByClass)
- [getChildByFilter](./Scene.html#getChildByFilter)
- [getChildByName](./Scene.html#getChildByName)
- [getChildrenByFilter](./Scene.html#getChildrenByFilter)
- [getChildrenByName](./Scene.html#getChildrenByName)
- [getComponent](./Scene.html#getComponent)
- [getElementById](./Scene.html#getElementById)
- [getNodeById](./Scene.html#getNodeById)
- [release](./Scene.html#release)
- [removeChild](./Scene.html#removeChild)
- [removeComponent](./Scene.html#removeComponent)
- [setAttribute](./Scene.html#setAttribute)
- [setId](./Scene.html#setId)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Scene**(`_type`, `triggerEvent`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `_type` | `string` |
| `triggerEvent` | `TFrameworkEventTrigger` |

#### [#](#Inherited-from) Inherited from

[Element](./Element.html).[constructor](./Element.html#constructor)

## [#](#Properties-2) Properties

### [#](#dataMapping) dataMapping

• `Readonly` **dataMapping**: `Object`

`Element`的数据映射。它是为了给组件的属性提供一个方便的用法，比如：

```
{
  position: [transform, position]
}
```

就是将`xml`中写在这个`Element`的`position`直接映射到了`transform`组件的`position`属性上。

**通常来讲，所有的驼峰如`nodeId`都会被映射为小写加中划线`node-id`**。

#### [#](#Index-signature) Index signature

▪ [key: `string`]: `string`[]

#### [#](#Inherited-from-2) Inherited from

[Element](./Element.html).[dataMapping](./Element.html#dataMapping)

---

### [#](#defaultComponents) defaultComponents

• `Readonly` **defaultComponents**: [`IEntityComponents`](./../interfaces/IEntityComponents.html)

`Element`的默认组件集合，详见[IEntityComponents](./../interfaces/IEntityComponents.html)。

#### [#](#Overrides) Overrides

[Element](./Element.html).[defaultComponents](./Element.html#defaultComponents)

---

### [#](#isScene) isScene

• `Readonly` **isScene**: `boolean` = `true`

---

### [#](#TYPE) TYPE

▪ `Static` **TYPE**: `string` = `'element'`

#### [#](#Inherited-from-3) Inherited from

[Element](./Element.html).[TYPE](./Element.html#TYPE)

## [#](#Accessors-2) Accessors

### [#](#animation) animation

• `get` **animation**(): [`AnimationSystem`](./AnimationSystem.html)

动画系统。

#### [#](#Returns) Returns

[`AnimationSystem`](./AnimationSystem.html)

---

### [#](#ar) ar

• `get` **ar**(): [`ARSystem`](./ARSystem.html)

AR系统。

#### [#](#Returns-2) Returns

[`ARSystem`](./ARSystem.html)

---

### [#](#assets) assets

• `get` **assets**(): [`AssetsSystem`](./AssetsSystem.html)

资源系统。

#### [#](#Returns-3) Returns

[`AssetsSystem`](./AssetsSystem.html)

---

### [#](#event) event

• `get` **event**(): [`EventManager`](./EventManager.html)

事件管理器。

#### [#](#Returns-4) Returns

[`EventManager`](./EventManager.html)

---

### [#](#frameHeight) frameHeight

• `get` **frameHeight**(): `number`

显示分辨率高。

#### [#](#Returns-5) Returns

`number`

---

### [#](#frameWidth) frameWidth

• `get` **frameWidth**(): `number`

显示分辨率宽。

#### [#](#Returns-6) Returns

`number`

---

### [#](#gizmo) gizmo

• `get` **gizmo**(): [`GizmoSystem`](./GizmoSystem.html)

Gizmo系统。

#### [#](#Returns-7) Returns

[`GizmoSystem`](./GizmoSystem.html)

---

### [#](#height) height

• `get` **height**(): `number`

渲染分辨率高，一般物理点击事件之类的都是参考这个。

#### [#](#Returns-8) Returns

`number`

---

### [#](#id) id

• `get` **id**(): `string`

写在`xml`上的那个`id`，要求唯一。

#### [#](#Returns-9) Returns

`string`

---

### [#](#inXML) inXML

• `get` **inXML**(): `boolean`

元素是否在`xml`中，若是`xr-shadow`下的节点，则为`false`。

#### [#](#Returns-10) Returns

`boolean`

---

### [#](#name) name

• `get` **name**(): `string`

名字，写在`xml`上的那个`name`，不唯一。

#### [#](#Returns-11) Returns

`string`

• `set` **name**(`value`): `void`

名字，写在`xml`上的那个`name`，不唯一。

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `value` | `string` |

#### [#](#Returns-12) Returns

`void`

---

### [#](#parent) parent

• `get` **parent**(): [`Element`](./Element.html)

父元素。

#### [#](#Returns-13) Returns

[`Element`](./Element.html)

---

### [#](#physics) physics

• `get` **physics**(): [`PhysicsSystem`](./PhysicsSystem.html)

物理系统。

#### [#](#Returns-14) Returns

[`PhysicsSystem`](./PhysicsSystem.html)

---

### [#](#ready) ready

• `get` **ready**(): `boolean`

场景是否已经就绪。

#### [#](#Returns-15) Returns

`boolean`

---

### [#](#render) render

• `get` **render**(): [`RenderSystem`](./RenderSystem.html)

渲染系统。

#### [#](#Returns-16) Returns

[`RenderSystem`](./RenderSystem.html)

---

### [#](#rootShadow) rootShadow

• `get` **rootShadow**(): [`XRShadow`](./XRShadow.html)

一个可以用于快速挂载自己创建的`Element`的`shadow`节点。

#### [#](#Returns-17) Returns

[`XRShadow`](./XRShadow.html)

---

### [#](#scene) scene

• `get` **scene**(): `this`

自身。

#### [#](#Returns-18) Returns

`this`

---

### [#](#share) share

• `get` **share**(): [`ShareSystem`](./ShareSystem.html)

分享系统。

#### [#](#Returns-19) Returns

[`ShareSystem`](./ShareSystem.html)

---

### [#](#timestamp) timestamp

• `get` **timestamp**(): `number`

当前时间戳(ms)。

#### [#](#Returns-20) Returns

`number`

---

### [#](#video) video

• `get` **video**(): [`VideoSystem`](./VideoSystem.html)

视频系统。

#### [#](#Returns-21) Returns

[`VideoSystem`](./VideoSystem.html)

---

### [#](#width) width

• `get` **width**(): `number`

渲染分辨率宽，一般物理点击事件之类的都是参考这个。

#### [#](#Returns-22) Returns

`number`

## [#](#Methods-2) Methods

### [#](#addChild) addChild

▸ **addChild**(`child`): `void`

手动添加一个子节点，**注意需要保证当前节点是`xr-shadow`或其子节点**。

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `child` | [`Element`](./Element.html) |

#### [#](#Returns-23) Returns

`void`

#### [#](#Inherited-from-4) Inherited from

[Element](./Element.html).[addChild](./Element.html#addChild)

---

### [#](#addComponent) addComponent

▸ **addComponent**<`T`>(`clz`, `options?`): `T`

手动添加一个`Component`。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Component`](./Component.html)<`any`, `T`> |

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `clz` | () => `T` |
| `options?` | `T`[`"__DATA_TYPE"`] |

#### [#](#Returns-24) Returns

`T`

#### [#](#Inherited-from-5) Inherited from

[Element](./Element.html).[addComponent](./Element.html#addComponent)

---

### [#](#createEffect) createEffect

▸ **createEffect**(`description`): [`Effect`](./Effect.html)

手动创建一个`Effect`资源。

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `description` | [`IEffectAsset`](./../interfaces/IEffectAsset.html) |

#### [#](#Returns-25) Returns

[`Effect`](./Effect.html)

---

### [#](#createElement) createElement

▸ **createElement**<`T`>(`clz`, `attributes?`): `T`

创建一个`Element`，但注意**其只能作为`xr-shadow`的子孙节点**，否则可能会出错！

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Element`](./Element.html)<`T`> |

#### [#](#Parameters-6) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `clz` | (...`args`: `any`) => `T` | - |
| `attributes?` | `Object` | 初始化的属性，同于`xml`中对应的标签属性。 |

#### [#](#Returns-26) Returns

`T`

---

### [#](#createGeometry) createGeometry

▸ **createGeometry**(`vertexLayout`, `vBuffer`, `iBuffer`, `indexType?`): [`Geometry`](./Geometry.html)

手动创建一个`Geometry`资源。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `vertexLayout` | `default` |
| `vBuffer` | `ArrayBufferView` |
| `iBuffer` | `ArrayBufferView` |
| `indexType?` | [`EIndexType`](./../enums/EIndexType.html) |

#### [#](#Returns-27) Returns

[`Geometry`](./Geometry.html)

---

### [#](#createImage) createImage

▸ **createImage**(`autoRelease?`): [`IImage`](./../interfaces/IImage.html)

手动创建一个`Image`资源。

#### [#](#Parameters-8) Parameters

| Name | Type | Default value | Description |
| --- | --- | --- | --- |
| `autoRelease` | `boolean` | `true` | 此图片在第一次时候后是否释放原始数据，默认释放。 |

#### [#](#Returns-28) Returns

[`IImage`](./../interfaces/IImage.html)

---

### [#](#createMaterial) createMaterial

▸ **createMaterial**(`effect`, `defaultUniforms?`): [`Material`](./Material.html)

手动创建一个`Material`资源。

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `effect` | [`Effect`](./Effect.html) |
| `defaultUniforms?` | `Object` |

#### [#](#Returns-29) Returns

[`Material`](./Material.html)

---

### [#](#createPostProcess) createPostProcess

▸ **createPostProcess**(`options`): [`PostProcess`](./PostProcess.html)

手动创建一个`PostProcess`资源。

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `options` | [`IPostProcessOptions`](./../interfaces/IPostProcessOptions.html) |

#### [#](#Returns-30) Returns

[`PostProcess`](./PostProcess.html)

---

### [#](#createRenderTexture) createRenderTexture

▸ **createRenderTexture**(`options?`): [`RenderTexture`](./RenderTexture.html)

手动创建一个`RenderTexture`资源。

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `options?` | [`IRenderTextureOptions`](./../interfaces/IRenderTextureOptions.html) |

#### [#](#Returns-31) Returns

[`RenderTexture`](./RenderTexture.html)

---

### [#](#createTexture) createTexture

▸ **createTexture**(`options`): `default`

手动创建一个`Texture`资源。

#### [#](#Parameters-12) Parameters

| Name | Type |
| --- | --- |
| `options` | [`ITextureOptions`](./../interfaces/ITextureOptions.html) |

#### [#](#Returns-32) Returns

`default`

---

### [#](#createUniformBlock) createUniformBlock

▸ **createUniformBlock**(`descriptor`): `default`

手动创建一个`UniformBlock`资源。

#### [#](#Parameters-13) Parameters

| Name | Type |
| --- | --- |
| `descriptor` | `default` |

#### [#](#Returns-33) Returns

`default`

---

### [#](#createUniformBlockDesc) createUniformBlockDesc

▸ **createUniformBlockDesc**(`options`): `default`

手动创建一个`UniformBlockDescriptor`资源。

#### [#](#Parameters-14) Parameters

| Name | Type |
| --- | --- |
| `options` | [`IUniformDescriptorOptions`](./../interfaces/IUniformDescriptorOptions.html) |

#### [#](#Returns-34) Returns

`default`

---

### [#](#createVertexLayout) createVertexLayout

▸ **createVertexLayout**(`options`): `default`

手动创建一个`VertexLayout`资源。

#### [#](#Parameters-15) Parameters

| Name | Type |
| --- | --- |
| `options` | [`IVertexLayoutOptions`](./../interfaces/IVertexLayoutOptions.html) |

#### [#](#Returns-35) Returns

`default`

---

### [#](#createVideoTexture) createVideoTexture

▸ **createVideoTexture**(`options?`): `Promise`<[`VideoTexture`](./VideoTexture.html)>

手动创建一个`VideoTexture`资源。

#### [#](#Parameters-16) Parameters

| Name | Type |
| --- | --- |
| `options?` | [`IVideoTextureOptions`](./../interfaces/IVideoTextureOptions.html) |

#### [#](#Returns-36) Returns

`Promise`<[`VideoTexture`](./VideoTexture.html)>

---

### [#](#dfs) dfs

▸ **dfs**<`T`>(`callback`, `defaultParams?`, `excludeRoot?`, `stop?`): `void`

递归遍历元素的所有子孙节点。

#### [#](#Type-parameters-3) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends `unknown` |

#### [#](#Parameters-17) Parameters

| Name | Type |
| --- | --- |
| `callback` | (`element`: [`Element`](./Element.html), `params?`: `T`) => `T` |
| `defaultParams?` | `T` |
| `excludeRoot?` | `boolean` |
| `stop` | (`element`: [`Element`](./Element.html), `params?`: `T`) => `boolean` |

#### [#](#Returns-37) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Element](./Element.html).[dfs](./Element.html#dfs)

---

### [#](#getChildAtIndex) getChildAtIndex

▸ **getChildAtIndex**<`T`>(`index`): `T`

获取第`index`个子元素。

#### [#](#Type-parameters-4) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Element`](./Element.html)<`T`> = [`Element`](./Element.html) |

#### [#](#Parameters-18) Parameters

| Name | Type |
| --- | --- |
| `index` | `number` |

#### [#](#Returns-38) Returns

`T`

#### [#](#Inherited-from-7) Inherited from

[Element](./Element.html).[getChildAtIndex](./Element.html#getChildAtIndex)

---

### [#](#getChildByClass) getChildByClass

▸ **getChildByClass**<`T`>(`clz`): `T`

通过元素的类获取子元素。

#### [#](#Type-parameters-5) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Element`](./Element.html)<`T`> = [`Element`](./Element.html) |

#### [#](#Parameters-19) Parameters

| Name | Type |
| --- | --- |
| `clz` | (...`args`: `any`[]) => `T` |

#### [#](#Returns-39) Returns

`T`

#### [#](#Inherited-from-8) Inherited from

[Element](./Element.html).[getChildByClass](./Element.html#getChildByClass)

---

### [#](#getChildByFilter) getChildByFilter

▸ **getChildByFilter**<`T`>(`filter`): `T`

通过`filter`获取子元素。

#### [#](#Type-parameters-6) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Element`](./Element.html)<`T`> = [`Element`](./Element.html) |

#### [#](#Parameters-20) Parameters

| Name | Type |
| --- | --- |
| `filter` | (`child`: [`Element`](./Element.html)) => `boolean` |

#### [#](#Returns-40) Returns

`T`

#### [#](#Inherited-from-9) Inherited from

[Element](./Element.html).[getChildByFilter](./Element.html#getChildByFilter)

---

### [#](#getChildByName) getChildByName

▸ **getChildByName**<`T`>(`name`): `T`

通过元素的名字`name`获取子元素。

#### [#](#Type-parameters-7) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Element`](./Element.html)<`T`> = [`Element`](./Element.html) |

#### [#](#Parameters-21) Parameters

| Name | Type |
| --- | --- |
| `name` | `string` |

#### [#](#Returns-41) Returns

`T`

#### [#](#Inherited-from-10) Inherited from

[Element](./Element.html).[getChildByName](./Element.html#getChildByName)

---

### [#](#getChildrenByFilter) getChildrenByFilter

▸ **getChildrenByFilter**(`filter`): [`Element`](./Element.html)[]

通过`filter`获取子元素列表。

#### [#](#Parameters-22) Parameters

| Name | Type |
| --- | --- |
| `filter` | (`child`: [`Element`](./Element.html)) => `boolean` |

#### [#](#Returns-42) Returns

[`Element`](./Element.html)[]

#### [#](#Inherited-from-11) Inherited from

[Element](./Element.html).[getChildrenByFilter](./Element.html#getChildrenByFilter)

---

### [#](#getChildrenByName) getChildrenByName

▸ **getChildrenByName**(`name`): [`Element`](./Element.html)[]

通过元素的名字`name`获取子元素们。

#### [#](#Parameters-23) Parameters

| Name | Type |
| --- | --- |
| `name` | `string` |

#### [#](#Returns-43) Returns

[`Element`](./Element.html)[]

#### [#](#Inherited-from-12) Inherited from

[Element](./Element.html).[getChildrenByName](./Element.html#getChildrenByName)

---

### [#](#getComponent) getComponent

▸ **getComponent**<`T`>(`clzName`): `T`

获取一个`Component`，可以使用类或者名字获取。

#### [#](#Type-parameters-8) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Component`](./Component.html)<`any`, `T`> |

#### [#](#Parameters-24) Parameters

| Name | Type |
| --- | --- |
| `clzName` | `string` |

#### [#](#Returns-44) Returns

`T`

#### [#](#Inherited-from-13) Inherited from

[Element](./Element.html).[getComponent](./Element.html#getComponent)

▸ **getComponent**<`T`>(`clz`): `T`

#### [#](#Type-parameters-9) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Component`](./Component.html)<`any`, `T`> |

#### [#](#Parameters-25) Parameters

| Name | Type |
| --- | --- |
| `clz` | () => `T` |

#### [#](#Returns-45) Returns

`T`

#### [#](#Inherited-from-14) Inherited from

[Element](./Element.html).[getComponent](./Element.html#getComponent)

---

### [#](#getElementById) getElementById

▸ **getElementById**(`id`): [`Element`](./Element.html)

通过在`wxml`的元素上设置的`id`索引一个元素，`id`是唯一的。

#### [#](#Parameters-26) Parameters

| Name | Type |
| --- | --- |
| `id` | `string` |

#### [#](#Returns-46) Returns

[`Element`](./Element.html)

---

### [#](#getNodeById) getNodeById

▸ **getNodeById**(`nodeId`): [`Transform`](./Transform.html)

通过在`wxml`的元素上设置的`node-id`索引一个`Transform`组件，`node-id`是唯一的。

#### [#](#Parameters-27) Parameters

| Name | Type |
| --- | --- |
| `nodeId` | `string` |

#### [#](#Returns-47) Returns

[`Transform`](./Transform.html)

---

### [#](#release) release

▸ **release**(): `void`

仅限自己创建的节点使用，否则后果自负。

#### [#](#Returns-48) Returns

`void`

#### [#](#Inherited-from-15) Inherited from

[Element](./Element.html).[release](./Element.html#release)

---

### [#](#removeChild) removeChild

▸ **removeChild**(`child`): `void`

手动移除一个子节点，**注意需要保证当前节点是`xr-shadow`或其子节点**。
**只调用removeChild没有办法走进子节点的onRelease里**，需要手动调用子节点的release才行。

#### [#](#Parameters-28) Parameters

| Name | Type |
| --- | --- |
| `child` | [`Element`](./Element.html) |

#### [#](#Returns-49) Returns

`void`

#### [#](#Inherited-from-16) Inherited from

[Element](./Element.html).[removeChild](./Element.html#removeChild)

---

### [#](#removeComponent) removeComponent

▸ **removeComponent**(`clz`): `void`

手动移除一个`Component`，注意保证其不在`xml`上。

#### [#](#Parameters-29) Parameters

| Name | Type |
| --- | --- |
| `clz` | () => [`Component`](./Component.html)<`any`> |

#### [#](#Returns-50) Returns

`void`

#### [#](#Inherited-from-17) Inherited from

[Element](./Element.html).[removeComponent](./Element.html#removeComponent)

---

### [#](#setAttribute) setAttribute

▸ **setAttribute**(`name`, `value`): `void`

设置一个属性，对应于`xml`标签中的那些属性，值为字符串。
**一般建议使用`component`的`setData`方法**！！！

#### [#](#Parameters-30) Parameters

| Name | Type |
| --- | --- |
| `name` | `string` |
| `value` | `string` |

#### [#](#Returns-51) Returns

`void`

#### [#](#Inherited-from-18) Inherited from

[Element](./Element.html).[setAttribute](./Element.html#setAttribute)

---

### [#](#setId) setId

▸ **setId**(`id`): `void`

仅限自己创建的节点使用，否则后果自负。

#### [#](#Parameters-31) Parameters

| Name | Type |
| --- | --- |
| `id` | `string` |

#### [#](#Returns-52) Returns

`void`

#### [#](#Inherited-from-19) Inherited from

[Element](./Element.html).[setId](./Element.html#setId)

Incorrect translation.