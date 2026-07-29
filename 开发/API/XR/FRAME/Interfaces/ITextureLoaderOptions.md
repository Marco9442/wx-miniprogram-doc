[xr-frame](./../) / [Exports](./../modules.html) / ITextureLoaderOptions

# [#](#Interface-ITextureLoaderOptions) Interface: ITextureLoaderOptions

[TextureLoader](./../classes/TextureLoader.html)可接受的自定义参数`schema`。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [anisoLevel](./ITextureLoaderOptions.html#anisoLevel)
- [generateMipmaps](./ITextureLoaderOptions.html#generateMipmaps)
- [magFilter](./ITextureLoaderOptions.html#magFilter)
- [minFilter](./ITextureLoaderOptions.html#minFilter)
- [wrapU](./ITextureLoaderOptions.html#wrapU)
- [wrapV](./ITextureLoaderOptions.html#wrapV)

## [#](#Properties-2) Properties

### [#](#anisoLevel) anisoLevel

• `Optional` **anisoLevel**: `number`

各向异性系数。

**`default`** 1

---

### [#](#generateMipmaps) generateMipmaps

• `Optional` **generateMipmaps**: `boolean`

是否要生成mipmaps。

**`default`** false

---

### [#](#magFilter) magFilter

• `Optional` **magFilter**: `number`

magFilter，值为数字，见[EFilterMode](./../enums/EFilterMode.html)。
默认值依据纹理是否POT而定。

---

### [#](#minFilter) minFilter

• `Optional` **minFilter**: `number`

minFilter，值为数字，见[EFilterMode](./../enums/EFilterMode.html)。
默认值依据纹理是否POT而定。

---

### [#](#wrapU) wrapU

• `Optional` **wrapU**: `number`

wrapU，值为数字，见[EWrapMode](./../enums/EWrapMode.html)。

**`default`** 2

---

### [#](#wrapV) wrapV

• `Optional` **wrapV**: `number`

wrapV，值为数字，见[EWrapMode](./../enums/EWrapMode.html)。

**`default`** 2

Incorrect translation.