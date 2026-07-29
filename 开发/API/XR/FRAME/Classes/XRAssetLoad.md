[xr-frame](./../) / [Exports](./../modules.html) / XRAssetLoad

# [#](#Class-XRAssetLoad) Class: XRAssetLoad

标签为`xr-asset-load`。

属性映射见[AssetLoadDataMapping](./../modules.html#AssetLoadDataMapping)。

## [#](#Hierarchy) Hierarchy

- [`Element`](./Element.html)

  ↳ **`XRAssetLoad`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./XRAssetLoad.html#constructor)

### [#](#Properties) Properties

- [dataMapping](./XRAssetLoad.html#dataMapping)
- [defaultComponents](./XRAssetLoad.html#defaultComponents)
- [neverTick](./XRAssetLoad.html#neverTick)
- [TYPE](./XRAssetLoad.html#TYPE)

### [#](#Accessors) Accessors

- [event](./XRAssetLoad.html#event)
- [id](./XRAssetLoad.html#id)
- [inXML](./XRAssetLoad.html#inXML)
- [name](./XRAssetLoad.html#name)
- [parent](./XRAssetLoad.html#parent)
- [scene](./XRAssetLoad.html#scene)

### [#](#Methods) Methods

- [addChild](./XRAssetLoad.html#addChild)
- [addComponent](./XRAssetLoad.html#addComponent)
- [dfs](./XRAssetLoad.html#dfs)
- [getChildAtIndex](./XRAssetLoad.html#getChildAtIndex)
- [getChildByClass](./XRAssetLoad.html#getChildByClass)
- [getChildByFilter](./XRAssetLoad.html#getChildByFilter)
- [getChildByName](./XRAssetLoad.html#getChildByName)
- [getChildrenByFilter](./XRAssetLoad.html#getChildrenByFilter)
- [getChildrenByName](./XRAssetLoad.html#getChildrenByName)
- [getComponent](./XRAssetLoad.html#getComponent)
- [release](./XRAssetLoad.html#release)
- [removeChild](./XRAssetLoad.html#removeChild)
- [removeComponent](./XRAssetLoad.html#removeComponent)
- [setAttribute](./XRAssetLoad.html#setAttribute)
- [setId](./XRAssetLoad.html#setId)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new XRAssetLoad**(`_type`, `triggerEvent`)

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

#### [#](#Overrides) Overrides

[Element](./Element.html).[dataMapping](./Element.html#dataMapping)

---

### [#](#defaultComponents) defaultComponents

• `Readonly` **defaultComponents**: [`IEntityComponents`](./../interfaces/IEntityComponents.html)

`Element`的默认组件集合，详见[IEntityComponents](./../interfaces/IEntityComponents.html)。

#### [#](#Inherited-from-2) Inherited from

[Element](./Element.html).[defaultComponents](./Element.html#defaultComponents)

---

### [#](#neverTick) neverTick

• `Readonly` **neverTick**: `boolean` = `true`

#### [#](#Overrides-2) Overrides

Element.neverTick

---

### [#](#TYPE) TYPE

▪ `Static` **TYPE**: `string` = `'element'`

#### [#](#Inherited-from-3) Inherited from

[Element](./Element.html).[TYPE](./Element.html#TYPE)

## [#](#Accessors-2) Accessors

### [#](#event) event

• `get` **event**(): [`EventManager`](./EventManager.html)

事件管理器。

#### [#](#Returns) Returns

[`EventManager`](./EventManager.html)

---

### [#](#id) id

• `get` **id**(): `string`

写在`xml`上的那个`id`，要求唯一。

#### [#](#Returns-2) Returns

`string`

---

### [#](#inXML) inXML

• `get` **inXML**(): `boolean`

元素是否在`xml`中，若是`xr-shadow`下的节点，则为`false`。

#### [#](#Returns-3) Returns

`boolean`

---

### [#](#name) name

• `get` **name**(): `string`

名字，写在`xml`上的那个`name`，不唯一。

#### [#](#Returns-4) Returns

`string`

• `set` **name**(`value`): `void`

名字，写在`xml`上的那个`name`，不唯一。

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `value` | `string` |

#### [#](#Returns-5) Returns

`void`

---

### [#](#parent) parent

• `get` **parent**(): [`Element`](./Element.html)

父元素。

#### [#](#Returns-6) Returns

[`Element`](./Element.html)

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

场景实例。

#### [#](#Returns-7) Returns

[`Scene`](./Scene.html)

## [#](#Methods-2) Methods

### [#](#addChild) addChild

▸ **addChild**(`child`): `void`

手动添加一个子节点，**注意需要保证当前节点是`xr-shadow`或其子节点**。

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `child` | [`Element`](./Element.html) |

#### [#](#Returns-8) Returns

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

#### [#](#Returns-9) Returns

`T`

#### [#](#Inherited-from-5) Inherited from

[Element](./Element.html).[addComponent](./Element.html#addComponent)

---

### [#](#dfs) dfs

▸ **dfs**<`T`>(`callback`, `defaultParams?`, `excludeRoot?`, `stop?`): `void`

递归遍历元素的所有子孙节点。

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends `unknown` |

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `callback` | (`element`: [`Element`](./Element.html), `params?`: `T`) => `T` |
| `defaultParams?` | `T` |
| `excludeRoot?` | `boolean` |
| `stop` | (`element`: [`Element`](./Element.html), `params?`: `T`) => `boolean` |

#### [#](#Returns-10) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Element](./Element.html).[dfs](./Element.html#dfs)

---

### [#](#getChildAtIndex) getChildAtIndex

▸ **getChildAtIndex**<`T`>(`index`): `T`

获取第`index`个子元素。

#### [#](#Type-parameters-3) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Element`](./Element.html)<`T`> = [`Element`](./Element.html) |

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `index` | `number` |

#### [#](#Returns-11) Returns

`T`

#### [#](#Inherited-from-7) Inherited from

[Element](./Element.html).[getChildAtIndex](./Element.html#getChildAtIndex)

---

### [#](#getChildByClass) getChildByClass

▸ **getChildByClass**<`T`>(`clz`): `T`

通过元素的类获取子元素。

#### [#](#Type-parameters-4) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Element`](./Element.html)<`T`> = [`Element`](./Element.html) |

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `clz` | (...`args`: `any`[]) => `T` |

#### [#](#Returns-12) Returns

`T`

#### [#](#Inherited-from-8) Inherited from

[Element](./Element.html).[getChildByClass](./Element.html#getChildByClass)

---

### [#](#getChildByFilter) getChildByFilter

▸ **getChildByFilter**<`T`>(`filter`): `T`

通过`filter`获取子元素。

#### [#](#Type-parameters-5) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Element`](./Element.html)<`T`> = [`Element`](./Element.html) |

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `filter` | (`child`: [`Element`](./Element.html)) => `boolean` |

#### [#](#Returns-13) Returns

`T`

#### [#](#Inherited-from-9) Inherited from

[Element](./Element.html).[getChildByFilter](./Element.html#getChildByFilter)

---

### [#](#getChildByName) getChildByName

▸ **getChildByName**<`T`>(`name`): `T`

通过元素的名字`name`获取子元素。

#### [#](#Type-parameters-6) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Element`](./Element.html)<`T`> = [`Element`](./Element.html) |

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `name` | `string` |

#### [#](#Returns-14) Returns

`T`

#### [#](#Inherited-from-10) Inherited from

[Element](./Element.html).[getChildByName](./Element.html#getChildByName)

---

### [#](#getChildrenByFilter) getChildrenByFilter

▸ **getChildrenByFilter**(`filter`): [`Element`](./Element.html)[]

通过`filter`获取子元素列表。

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `filter` | (`child`: [`Element`](./Element.html)) => `boolean` |

#### [#](#Returns-15) Returns

[`Element`](./Element.html)[]

#### [#](#Inherited-from-11) Inherited from

[Element](./Element.html).[getChildrenByFilter](./Element.html#getChildrenByFilter)

---

### [#](#getChildrenByName) getChildrenByName

▸ **getChildrenByName**(`name`): [`Element`](./Element.html)[]

通过元素的名字`name`获取子元素们。

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `name` | `string` |

#### [#](#Returns-16) Returns

[`Element`](./Element.html)[]

#### [#](#Inherited-from-12) Inherited from

[Element](./Element.html).[getChildrenByName](./Element.html#getChildrenByName)

---

### [#](#getComponent) getComponent

▸ **getComponent**<`T`>(`clzName`): `T`

获取一个`Component`，可以使用类或者名字获取。

#### [#](#Type-parameters-7) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Component`](./Component.html)<`any`, `T`> |

#### [#](#Parameters-12) Parameters

| Name | Type |
| --- | --- |
| `clzName` | `string` |

#### [#](#Returns-17) Returns

`T`

#### [#](#Inherited-from-13) Inherited from

[Element](./Element.html).[getComponent](./Element.html#getComponent)

▸ **getComponent**<`T`>(`clz`): `T`

#### [#](#Type-parameters-8) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Component`](./Component.html)<`any`, `T`> |

#### [#](#Parameters-13) Parameters

| Name | Type |
| --- | --- |
| `clz` | () => `T` |

#### [#](#Returns-18) Returns

`T`

#### [#](#Inherited-from-14) Inherited from

[Element](./Element.html).[getComponent](./Element.html#getComponent)

---

### [#](#release) release

▸ **release**(): `void`

仅限自己创建的节点使用，否则后果自负。

#### [#](#Returns-19) Returns

`void`

#### [#](#Inherited-from-15) Inherited from

[Element](./Element.html).[release](./Element.html#release)

---

### [#](#removeChild) removeChild

▸ **removeChild**(`child`): `void`

手动移除一个子节点，**注意需要保证当前节点是`xr-shadow`或其子节点**。
**只调用removeChild没有办法走进子节点的onRelease里**，需要手动调用子节点的release才行。

#### [#](#Parameters-14) Parameters

| Name | Type |
| --- | --- |
| `child` | [`Element`](./Element.html) |

#### [#](#Returns-20) Returns

`void`

#### [#](#Inherited-from-16) Inherited from

[Element](./Element.html).[removeChild](./Element.html#removeChild)

---

### [#](#removeComponent) removeComponent

▸ **removeComponent**(`clz`): `void`

手动移除一个`Component`，注意保证其不在`xml`上。

#### [#](#Parameters-15) Parameters

| Name | Type |
| --- | --- |
| `clz` | () => [`Component`](./Component.html)<`any`> |

#### [#](#Returns-21) Returns

`void`

#### [#](#Inherited-from-17) Inherited from

[Element](./Element.html).[removeComponent](./Element.html#removeComponent)

---

### [#](#setAttribute) setAttribute

▸ **setAttribute**(`name`, `value`): `void`

设置一个属性，对应于`xml`标签中的那些属性，值为字符串。
**一般建议使用`component`的`setData`方法**！！！

#### [#](#Parameters-16) Parameters

| Name | Type |
| --- | --- |
| `name` | `string` |
| `value` | `string` |

#### [#](#Returns-22) Returns

`void`

#### [#](#Inherited-from-18) Inherited from

[Element](./Element.html).[setAttribute](./Element.html#setAttribute)

---

### [#](#setId) setId

▸ **setId**(`id`): `void`

仅限自己创建的节点使用，否则后果自负。

#### [#](#Parameters-17) Parameters

| Name | Type |
| --- | --- |
| `id` | `string` |

#### [#](#Returns-23) Returns

`void`

#### [#](#Inherited-from-19) Inherited from

[Element](./Element.html).[setId](./Element.html#setId)

Incorrect translation.