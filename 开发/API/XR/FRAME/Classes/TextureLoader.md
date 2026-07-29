[xr-frame](./../) / [Exports](./../modules.html) / TextureLoader

# [#](#Class-TextureLoader) Class: TextureLoader

纹理资源[Texture](./../modules.html#Texture)的加载器。

内置资源可以通过[registerTexture](./../modules.html#registerTexture)注册，拥有内置资源`brdf-lut`、`white`、`transparent`、`black`、`red`、`green`、`blue`、`yellow`、`babyblue`、`babygreen`、`babyred`。

## [#](#Hierarchy) Hierarchy

- [`AssetLoader`](./AssetLoader.html)<`Kanata.Texture`, [`ITextureLoaderOptions`](./../interfaces/ITextureLoaderOptions.html)>

  ↳ **`TextureLoader`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./TextureLoader.html#constructor)

### [#](#Properties) Properties

- [schema](./TextureLoader.html#schema)

### [#](#Accessors) Accessors

- [scene](./TextureLoader.html#scene)

### [#](#Methods) Methods

- [cancel](./TextureLoader.html#cancel)
- [getBuiltin](./TextureLoader.html#getBuiltin)
- [load](./TextureLoader.html#load)
- [release](./TextureLoader.html#release)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new TextureLoader**(`_scene`, `type`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `_scene` | [`Scene`](./Scene.html) |
| `type` | `string` |

#### [#](#Inherited-from) Inherited from

[AssetLoader](./AssetLoader.html).[constructor](./AssetLoader.html#constructor)

## [#](#Properties-2) Properties

### [#](#schema) schema

• `Readonly` **schema**: [`ILoaderOptionsSchema`](./../interfaces/ILoaderOptionsSchema.html)

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
| `params` | `IAssetLoadData`<[`ITextureLoaderOptions`](./../interfaces/ITextureLoaderOptions.html)> |

#### [#](#Returns-2) Returns

`void`

#### [#](#Inherited-from-2) Inherited from

[AssetLoader](./AssetLoader.html).[cancel](./AssetLoader.html#cancel)

---

### [#](#getBuiltin) getBuiltin

▸ **getBuiltin**(): { `assetId`: `string` = 'brdf-lut'; `options`: {} = {}; `src`: `string` = 'https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/brdflut.png' }[]

返回默认资源列表。
所有默认资源都是惰性加载的。

#### [#](#Returns-3) Returns

{ `assetId`: `string` = 'brdf-lut'; `options`: {} = {}; `src`: `string` = 'https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/brdflut.png' }[]

#### [#](#Overrides-2) Overrides

[AssetLoader](./AssetLoader.html).[getBuiltin](./AssetLoader.html#getBuiltin)

---

### [#](#load) load

▸ **load**(`params`, `callbacks`): `void`

加载一个资源，并根据情况执行`callbacks`中的回调。
**理论上必须要实现！**

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `params` | `ITextureLoadData` |
| `callbacks` | `Object` |
| `callbacks.onError` | (`error`: `Error`) => `void` |
| `callbacks.onLoaded` | (`value`: `default`) => `void` |
| `callbacks.onLoading` | (`progress`: `number`) => `void` |

#### [#](#Returns-4) Returns

`void`

#### [#](#Overrides-3) Overrides

[AssetLoader](./AssetLoader.html).[load](./AssetLoader.html#load)

---

### [#](#release) release

▸ **release**(`params`, `value`): `void`

释放资源时将会调用，用于自定义释放逻辑。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `params` | `ITextureLoadData` |
| `value` | `default` |

#### [#](#Returns-5) Returns

`void`

#### [#](#Overrides-4) Overrides

[AssetLoader](./AssetLoader.html).[release](./AssetLoader.html#release)

Incorrect translation.