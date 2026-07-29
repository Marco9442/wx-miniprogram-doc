[xr-frame](./../) / [Exports](./../modules.html) / AssetLoader

# [#](#Class-AssetLoader-T-ILoadOptions) Class: AssetLoader<T, ILoadOptions>

资源加载器的基类，配合[AssetsSystem](./AssetsSystem.html)使用。
在基础库版本**v2.29.2**以上导出。

## [#](#Type-parameters) Type parameters

| Name | Description |
| --- | --- |
| `T` | 加载资源的类型。 |
| `ILoadOptions` | 可接受额外配置的类型。 |

## [#](#Hierarchy) Hierarchy

- **`AssetLoader`**

  ↳ [`TextureLoader`](./TextureLoader.html)

  ↳ [`ImageLoader`](./ImageLoader.html)

  ↳ [`CubeTextureLoader`](./CubeTextureLoader.html)

  ↳ [`VideoTextureLoader`](./VideoTextureLoader.html)

  ↳ [`EnvDataLoader`](./EnvDataLoader.html)

  ↳ [`GLTFLoader`](./GLTFLoader.html)

  ↳ [`KeyframeLoader`](./KeyframeLoader.html)

  ↳ [`RawLoader`](./RawLoader.html)

  ↳ [`AtlasLoader`](./AtlasLoader.html)

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./AssetLoader.html#constructor)

### [#](#Properties) Properties

- [schema](./AssetLoader.html#schema)

### [#](#Accessors) Accessors

- [scene](./AssetLoader.html#scene)

### [#](#Methods) Methods

- [cancel](./AssetLoader.html#cancel)
- [getBuiltin](./AssetLoader.html#getBuiltin)
- [load](./AssetLoader.html#load)
- [release](./AssetLoader.html#release)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new AssetLoader**<`T`, `ILoadOptions`>(`_scene`, `type`)

#### [#](#Type-parameters-2) Type parameters

| Name |
| --- |
| `T` |
| `ILoadOptions` |

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `_scene` | [`Scene`](./Scene.html) |
| `type` | `string` |

## [#](#Properties-2) Properties

### [#](#schema) schema

• `Readonly` **schema**: [`ILoaderOptionsSchema`](./../interfaces/ILoaderOptionsSchema.html) = `{}`

和[Component.schema](./Component.html#schema)类似，指定解析Options的实际`schema`，对应于`ILoadOptions`。

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
| `params` | `IAssetLoadData`<`ILoadOptions`> |

#### [#](#Returns-2) Returns

`void`

---

### [#](#getBuiltin) getBuiltin

▸ **getBuiltin**(): { `assetId`: `string` ; `options`: `ILoadOptions` ; `src`: `string` }[]

返回默认资源列表。
所有默认资源都是惰性加载的。

#### [#](#Returns-3) Returns

{ `assetId`: `string` ; `options`: `ILoadOptions` ; `src`: `string` }[]

---

### [#](#load) load

▸ **load**(`data`, `callbacks`): `void`

加载一个资源，并根据情况执行`callbacks`中的回调。
**理论上必须要实现！**

#### [#](#Parameters-3) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `data` | `IAssetLoadData`<`ILoadOptions`> | - |
| `callbacks` | `Object` | 开发者需要在加载进度更新时执行`onLoading`，在加载完成时执行`onLoaded`，在加载出错是执行`onError` |
| `callbacks.onError` | (`error`: `Error`) => `void` | - |
| `callbacks.onLoaded` | (`result`: `T`, `localPath?`: `string`) => `void` | - |
| `callbacks.onLoading` | (`progress`: `number`) => `void` | - |

#### [#](#Returns-4) Returns

`void`

---

### [#](#release) release

▸ **release**(`params`, `value`): `void`

释放资源时将会调用，用于自定义释放逻辑。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `params` | `IAssetLoadData`<`ILoadOptions`> |
| `value` | `T` |

#### [#](#Returns-5) Returns

`void`

Incorrect translation.