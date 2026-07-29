[xr-frame](./../) / [Exports](./../modules.html) / KeyframeLoader

# [#](#Class-KeyframeLoader) Class: KeyframeLoader

帧动画资源[KeyframeAnimation](./KeyframeAnimation.html)的加载器。

## [#](#Hierarchy) Hierarchy

- [`AssetLoader`](./AssetLoader.html)<[`KeyframeAnimation`](./KeyframeAnimation.html), [`IKeyframeLoaderOptions`](./../interfaces/IKeyframeLoaderOptions.html)>

  ↳ **`KeyframeLoader`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./KeyframeLoader.html#constructor)

### [#](#Properties) Properties

- [schema](./KeyframeLoader.html#schema)

### [#](#Accessors) Accessors

- [scene](./KeyframeLoader.html#scene)

### [#](#Methods) Methods

- [cancel](./KeyframeLoader.html#cancel)
- [getBuiltin](./KeyframeLoader.html#getBuiltin)
- [load](./KeyframeLoader.html#load)
- [release](./KeyframeLoader.html#release)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new KeyframeLoader**(`_scene`, `type`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `_scene` | [`Scene`](./Scene.html) |
| `type` | `string` |

#### [#](#Inherited-from) Inherited from

[AssetLoader](./AssetLoader.html).[constructor](./AssetLoader.html#constructor)

## [#](#Properties-2) Properties

### [#](#schema) schema

• `Readonly` **schema**: [`ILoaderOptionsSchema`](./../interfaces/ILoaderOptionsSchema.html) = `{}`

和[Component.schema](./Component.html#schema)类似，指定解析Options的实际`schema`，对应于`ILoadOptions`。

#### [#](#Overrides) Overrides

[AssetLoader](./AssetLoader.html).[schema](./AssetLoader.html#schema)

## [#](#Accessors-2) Accessors

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前资源所属场景的实例。

#### [#](#Returns) Returns

[`Scene`](./Scene.html)

## [#](#Methods-2) Methods

### [#](#cancel) cancel

▸ **cancel**(`params`): `void`

取消加载特定资源。一般不需要自己编写逻辑，而是使用`entity.canceled`在加载终点丢弃。
注意`entity.canceled`是在这里赋值的，所以一般继承请务必先执行`super.cancel()`！

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `params` | `IAssetLoadData`<[`IKeyframeLoaderOptions`](./../interfaces/IKeyframeLoaderOptions.html)> |

#### [#](#Returns-2) Returns

`void`

#### [#](#Inherited-from-2) Inherited from

[AssetLoader](./AssetLoader.html).[cancel](./AssetLoader.html#cancel)

---

### [#](#getBuiltin) getBuiltin

▸ **getBuiltin**(): { `assetId`: `string` ; `options`: [`IKeyframeLoaderOptions`](./../interfaces/IKeyframeLoaderOptions.html) ; `src`: `string` }[]

返回默认资源列表。
所有默认资源都是惰性加载的。

#### [#](#Returns-3) Returns

{ `assetId`: `string` ; `options`: [`IKeyframeLoaderOptions`](./../interfaces/IKeyframeLoaderOptions.html) ; `src`: `string` }[]

#### [#](#Inherited-from-3) Inherited from

[AssetLoader](./AssetLoader.html).[getBuiltin](./AssetLoader.html#getBuiltin)

---

### [#](#load) load

▸ **load**(`params`, `callbacks`): `Promise`<`void`>

加载一个资源，并根据情况执行`callbacks`中的回调。
**理论上必须要实现！**

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `params` | `IKeyframeLoadData` |
| `callbacks` | `Object` |
| `callbacks.onError` | (`error`: `Error`) => `void` |
| `callbacks.onLoaded` | (`value`: [`KeyframeAnimation`](./KeyframeAnimation.html)) => `void` |
| `callbacks.onLoading` | (`progress`: `number`) => `void` |

#### [#](#Returns-4) Returns

`Promise`<`void`>

#### [#](#Overrides-2) Overrides

[AssetLoader](./AssetLoader.html).[load](./AssetLoader.html#load)

---

### [#](#release) release

▸ **release**(`params`, `value`): `void`

释放资源时将会调用，用于自定义释放逻辑。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `params` | `IAssetLoadData`<[`IKeyframeLoaderOptions`](./../interfaces/IKeyframeLoaderOptions.html)> |
| `value` | [`KeyframeAnimation`](./KeyframeAnimation.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-4) Inherited from

[AssetLoader](./AssetLoader.html).[release](./AssetLoader.html#release)

Incorrect translation.