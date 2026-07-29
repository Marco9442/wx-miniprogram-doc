[xr-frame](./../) / [Exports](./../modules.html) / Atlas

# [#](#Class-Atlas) Class: Atlas

图集资源。

**`version`** 2.27.1

一般通过[AtlasLoader](./AtlasLoader.html)加载自动生成。
推荐使用[Shoebox](https://www.renderhjs.net/shoebox/)等工具生成。

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Atlas.html#constructor)

### [#](#Properties) Properties

- [isAtlas](./Atlas.html#isAtlas)

### [#](#Accessors) Accessors

- [frames](./Atlas.html#frames)
- [meta](./Atlas.html#meta)
- [texture](./Atlas.html#texture)

### [#](#Methods) Methods

- [getFrame](./Atlas.html#getFrame)
- [getUVMatrix](./Atlas.html#getUVMatrix)
- [getUVST](./Atlas.html#getUVST)
- [updateFrame](./Atlas.html#updateFrame)
- [CREATE\_FROM\_GRIDS](./Atlas.html#CREATE_FROM_GRIDS)
- [CREATE\_FROM\_TEXTURE](./Atlas.html#CREATE_FROM_TEXTURE)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Atlas**(`_scene`, `options`)

构建一个图集。

#### [#](#Parameters) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `_scene` | [`Scene`](./Scene.html) | - |
| `options` | [`IAtlasOptions`](./../interfaces/IAtlasOptions.html) | 初始化参数。 |

## [#](#Properties-2) Properties

### [#](#isAtlas) isAtlas

• **isAtlas**: `boolean` = `true`

## [#](#Accessors-2) Accessors

### [#](#frames) frames

• `get` **frames**(): `Object`

获取帧集合。

#### [#](#Returns) Returns

`Object`

---

### [#](#meta) meta

• `get` **meta**(): `Object`

获取元信息。

#### [#](#Returns-2) Returns

`Object`

| Name | Type |
| --- | --- |
| `size` | { `h`: `number` ; `w`: `number` } |
| `size.h` | `number` |
| `size.w` | `number` |

---

### [#](#texture) texture

• `get` **texture**(): `default`

获取整体的纹理。

#### [#](#Returns-3) Returns

`default`

## [#](#Methods-2) Methods

### [#](#getFrame) getFrame

▸ **getFrame**(`frameName`): `Object`

获取某一帧的数据。

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `frameName` | `string` |

#### [#](#Returns-4) Returns

`Object`

| Name | Type |
| --- | --- |
| `h` | `number` |
| `w` | `number` |
| `x` | `number` |
| `y` | `number` |

---

### [#](#getUVMatrix) getUVMatrix

▸ **getUVMatrix**(`frameName`): [`Matrix3`](./Matrix3.html)

获取某一帧的uv变换矩阵。

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `frameName` | `string` |

#### [#](#Returns-5) Returns

[`Matrix3`](./Matrix3.html)

---

### [#](#getUVST) getUVST

▸ **getUVST**(`frameName`): [`Vector4`](./Vector4.html)

获取某一帧的uvST。
[sx, sy, tx, ty]。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `frameName` | `string` |

#### [#](#Returns-6) Returns

[`Vector4`](./Vector4.html)

---

### [#](#updateFrame) updateFrame

▸ **updateFrame**(`frameName`, `onUpdate`): `void`

更新某一frame，通过`onUpdate`方法参数中的`texture`和`region`来更新上此帧所占据区域内的图像。

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `frameName` | `string` |
| `onUpdate` | (`texture`: `default`, `region`: { `h`: `number` ; `w`: `number` ; `x`: `number` ; `y`: `number` }, `frameName`: `string`) => `void` |

#### [#](#Returns-7) Returns

`void`

---

### [#](#CREATE-FROM-GRIDS) CREATE\_FROM\_GRIDS

▸ `Static` **CREATE\_FROM\_GRIDS**(`scene`, `options`, `onUpdate?`): [`Atlas`](./Atlas.html)

根据宽高和行数、列数来创建一个空的图集。
这个图集将被行列分成若干个格子帧，开发者可以根据实际状况去使用`updateFrame`更新这些格子。
自动生成的帧的名字为`${row}${col}`，比如第一行第一列为`'11'`。

#### [#](#Parameters-6) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `scene` | [`Scene`](./Scene.html) | - |
| `options` | `Object` | - |
| `options.cols` | `number` | - |
| `options.height` | `number` | - |
| `options.rows` | `number` | - |
| `options.space?` | `number` | - |
| `options.width` | `number` | - |
| `onUpdate?` | (`texture`: `default`, `region`: { `col`: `number` ; `h`: `number` ; `row`: `number` ; `w`: `number` ; `x`: `number` ; `y`: `number` }, `frameName`: `string`) => `void` | 初始化时的回调，可以用于一开始绘制图像 |

#### [#](#Returns-8) Returns

[`Atlas`](./Atlas.html)

---

### [#](#CREATE-FROM-TEXTURE) CREATE\_FROM\_TEXTURE

▸ `Static` **CREATE\_FROM\_TEXTURE**(`scene`, `texture`, `options`): [`Atlas`](./Atlas.html)

根据纹理和配置，来通过纹理创建一个不可修改的图集。通常用于精灵动画。
这个图集将被行列分成若干个格子帧，每一帧的名字为`0`、`1`、`2`......

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `scene` | [`Scene`](./Scene.html) |
| `texture` | `default` |
| `options` | [`IAtlasCreationOptions`](./../interfaces/IAtlasCreationOptions.html) |

#### [#](#Returns-9) Returns

[`Atlas`](./Atlas.html)

Incorrect translation.