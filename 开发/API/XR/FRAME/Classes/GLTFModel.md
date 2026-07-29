[xr-frame](./../) / [Exports](./../modules.html) / GLTFModel

# [#](#Class-GLTFModel) Class: GLTFModel

加载完毕的GLTF模型，可以在节点下创建[GLTF组件](./GLTF.html)来将其实例化。

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./GLTFModel.html#constructor)

### [#](#Properties) Properties

- [jsonRaw](./GLTFModel.html#jsonRaw)

### [#](#Methods) Methods

- [createFromBuffer](./GLTFModel.html#createFromBuffer)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new GLTFModel**(`_scene`, `model`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `_scene` | [`Scene`](./Scene.html) |
| `model` | `GLTFRootLoaded` |

## [#](#Properties-2) Properties

### [#](#jsonRaw) jsonRaw

• `Readonly` **jsonRaw**: `object`

如果IGLTFLoaderOptions里开启了preserveRaw，则会将原始json保存下来。

## [#](#Methods-2) Methods

### [#](#createFromBuffer) createFromBuffer

▸ `Static` **createFromBuffer**(`scene`, `buffer`, `options`): `Promise`<[`GLTFModel`](./GLTFModel.html)>

使用GLB文件加载而成的buffer，来生成GLTF模型。

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `scene` | [`Scene`](./Scene.html) |
| `buffer` | `ArrayBuffer` |
| `options` | [`IGLTFLoaderOptions`](./../interfaces/IGLTFLoaderOptions.html) |

#### [#](#Returns) Returns

`Promise`<[`GLTFModel`](./GLTFModel.html)>

Incorrect translation.