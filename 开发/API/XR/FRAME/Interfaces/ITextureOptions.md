[xr-frame](./../) / [Exports](./../modules.html) / ITextureOptions

# [#](#Interface-ITextureOptions) Interface: ITextureOptions

纹理资源[Texture](./../modules.html#Texture)的创建参数。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [anisoLevel](./ITextureOptions.html#anisoLevel)
- [generateMipmaps](./ITextureOptions.html#generateMipmaps)
- [height](./ITextureOptions.html#height)
- [magFilter](./ITextureOptions.html#magFilter)
- [minFilter](./ITextureOptions.html#minFilter)
- [mips](./ITextureOptions.html#mips)
- [offsets](./ITextureOptions.html#offsets)
- [pixelFormat](./ITextureOptions.html#pixelFormat)
- [slices](./ITextureOptions.html#slices)
- [source](./ITextureOptions.html#source)
- [type](./ITextureOptions.html#type)
- [width](./ITextureOptions.html#width)
- [wrapU](./ITextureOptions.html#wrapU)
- [wrapV](./ITextureOptions.html#wrapV)
- [wrapW](./ITextureOptions.html#wrapW)

## [#](#Properties-2) Properties

### [#](#anisoLevel) anisoLevel

• `Optional` **anisoLevel**: `number`

各向异性等级。

---

### [#](#generateMipmaps) generateMipmaps

• `Optional` **generateMipmaps**: `boolean`

是否要自动生成`mipmaps`，仅对非压缩纹理有效。

---

### [#](#height) height

• `Optional` **height**: `number`

纹理高，如果`source`是`IImage`可以不传。

---

### [#](#magFilter) magFilter

• `Optional` **magFilter**: [`EFilterMode`](./../enums/EFilterMode.html)

---

### [#](#minFilter) minFilter

• `Optional` **minFilter**: [`EFilterMode`](./../enums/EFilterMode.html)

---

### [#](#mips) mips

• `Optional` **mips**: `number`

纹理有多少级`mipmap`。

---

### [#](#offsets) offsets

• `Optional` **offsets**: `Uint32Array`

当`source`为`Buffer`纹理并且拥有`mipmaps`之类的时，标记如何切割数据。
规则是: off1, size1, off2, size2......

---

### [#](#pixelFormat) pixelFormat

• `Optional` **pixelFormat**: [`ETextureFormat`](./../enums/ETextureFormat.html)

纹理的像素格式。

---

### [#](#slices) slices

• `Optional` **slices**: `number`

纹理有多少切片，比如立方体纹理就为`6`。

---

### [#](#source) source

• `Optional` **source**: `TTextureSource`[]

纹理数据源，如果是2D纹理，一般只能有一个元素。如果是`Buffer`类型数据，比如压缩纹理，则需要和`offsets`配合使用，一般用于`mipmaps`的场合。
如果是立方体纹理，则有六个元素。

---

### [#](#type) type

• `Optional` **type**: [`ETextureType`](./../enums/ETextureType.html)

纹理类型。

---

### [#](#width) width

• `Optional` **width**: `number`

纹理宽，如果`source`是`IImage`可以不传。

---

### [#](#wrapU) wrapU

• `Optional` **wrapU**: [`EWrapMode`](./../enums/EWrapMode.html)

---

### [#](#wrapV) wrapV

• `Optional` **wrapV**: [`EWrapMode`](./../enums/EWrapMode.html)

---

### [#](#wrapW) wrapW

• `Optional` **wrapW**: [`EWrapMode`](./../enums/EWrapMode.html)

Incorrect translation.