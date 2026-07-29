[xr-frame](./../) / [Exports](./../modules.html) / IImage

# [#](#Interface-IImage) Interface: IImage

引擎原生图片接口。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [autoRelease](./IImage.html#autoRelease)
- [data](./IImage.html#data)
- [height](./IImage.html#height)
- [localPath](./IImage.html#localPath)
- [onerror](./IImage.html#onerror)
- [onload](./IImage.html#onload)
- [premultiplyAlpha](./IImage.html#premultiplyAlpha)
- [src](./IImage.html#src)
- [type](./IImage.html#type)
- [width](./IImage.html#width)

## [#](#Properties-2) Properties

### [#](#autoRelease) autoRelease

• `Optional` **autoRelease**: `boolean`

对于`ArrayBuffer`创建的图片，第一次使用后是否要自动释放内存，在`xr-frame`中，默认自动释放。

---

### [#](#data) data

• `Optional` `Readonly` **data**: `ArrayBuffer` | `HTMLImageElement`

解码数据，视不同Backend而定。

---

### [#](#height) height

• **height**: `number`

图片高度。

---

### [#](#localPath) localPath

• `Optional` **localPath**: `string`

图片本地缓存地址，仅在微信内有用。

---

### [#](#onerror) onerror

• **onerror**: (`error`: `Error`) => `void`

#### [#](#Type-declaration) Type declaration

▸ (`error`): `void`

出错的回调。

##### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `error` | `Error` |

##### [#](#Returns) Returns

`void`

---

### [#](#onload) onload

• **onload**: () => `void`

#### [#](#Type-declaration-2) Type declaration

▸ (): `void`

加载完成的回调。

##### [#](#Returns-2) Returns

`void`

---

### [#](#premultiplyAlpha) premultiplyAlpha

• **premultiplyAlpha**: `boolean`

是否要预乘Alpha。

---

### [#](#src) src

• **src**: `string` | `ArrayBufferView` | `ArrayBuffer`

图片地址或者待解码的ArrayBuffer。

---

### [#](#type) type

• `Optional` **type**: `string`

图片源于ArrayBuffer时，传入的mimetype。

---

### [#](#width) width

• **width**: `number`

图片宽度。

Incorrect translation.