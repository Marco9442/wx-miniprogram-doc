[xr-frame](./../) / [Exports](./../modules.html) / IAtlasOptions

# [#](#Interface-IAtlasOptions) Interface: IAtlasOptions

`Atlas`的初始化参数类型。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [frames](./IAtlasOptions.html#frames)
- [image](./IAtlasOptions.html#image)
- [meta](./IAtlasOptions.html#meta)
- [texture](./IAtlasOptions.html#texture)

## [#](#Properties-2) Properties

### [#](#frames) frames

• **frames**: `Object`

帧定义，若不指定`uv`则会自动按比例计算。

#### [#](#Index-signature) Index signature

▪ [key: `string`]: { `frame`: { `h`: `number` ; `w`: `number` ; `x`: `number` ; `y`: `number` } }

---

### [#](#image) image

• `Optional` **image**: [`IImage`](./IImage.html)

图片。

---

### [#](#meta) meta

• **meta**: `Object`

原信息，主要定义图片尺寸。

#### [#](#Type-declaration) Type declaration

| Name | Type |
| --- | --- |
| `size` | { `h`: `number` ; `w`: `number` } |
| `size.h` | `number` |
| `size.w` | `number` |

---

### [#](#texture) texture

• `Optional` **texture**: `default`

也可以直接传入一张纹理。

Incorrect translation.