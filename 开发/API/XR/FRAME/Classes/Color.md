[xr-frame](./../) / [Exports](./../modules.html) / Color

# [#](#Class-Color) Class: Color

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Color.html#constructor)

### [#](#Properties) Properties

- [BlendType](./Color.html#BlendType)

### [#](#Accessors) Accessors

- [a](./Color.html#a)
- [b](./Color.html#b)
- [g](./Color.html#g)
- [r](./Color.html#r)
- [BLACK](./Color.html#BLACK)
- [TRANSPARENT](./Color.html#TRANSPARENT)
- [WHITE](./Color.html#WHITE)

### [#](#Methods) Methods

- [clone](./Color.html#clone)
- [equals](./Color.html#equals)
- [mix](./Color.html#mix)
- [set](./Color.html#set)
- [setRGBA](./Color.html#setRGBA)
- [setValue32](./Color.html#setValue32)
- [toNormalizedArray](./Color.html#toNormalizedArray)
- [toRGBAString](./Color.html#toRGBAString)
- [blendColorHex](./Color.html#blendColorHex)
- [diffc](./Color.html#diffc)
- [fromFloatArray](./Color.html#fromFloatArray)
- [fromHex](./Color.html#fromHex)
- [fromHexString](./Color.html#fromHexString)
- [getValue32FromHSVA](./Color.html#getValue32FromHSVA)
- [getValue32FromRGBA](./Color.html#getValue32FromRGBA)
- [hsvV2rgb](./Color.html#hsvV2rgb)
- [multiplyColorHex](./Color.html#multiplyColorHex)
- [percentRoundFn](./Color.html#percentRoundFn)
- [randomMix](./Color.html#randomMix)
- [rgb2hsv](./Color.html#rgb2hsv)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Color**(`r?`, `g?`, `b?`, `a?`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `r?` | `number` |
| `g?` | `number` |
| `b?` | `number` |
| `a?` | `number` |

## [#](#Properties-2) Properties

### [#](#BlendType) BlendType

▪ `Static` **BlendType**: typeof `BlendType`

## [#](#Accessors-2) Accessors

### [#](#a) a

• `get` **a**(): `number`

#### [#](#Returns) Returns

`number`

• `set` **a**(`val`): `void`

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `val` | `number` |

#### [#](#Returns-2) Returns

`void`

---

### [#](#b) b

• `get` **b**(): `number`

#### [#](#Returns-3) Returns

`number`

• `set` **b**(`val`): `void`

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `val` | `number` |

#### [#](#Returns-4) Returns

`void`

---

### [#](#g) g

• `get` **g**(): `number`

#### [#](#Returns-5) Returns

`number`

• `set` **g**(`val`): `void`

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `val` | `number` |

#### [#](#Returns-6) Returns

`void`

---

### [#](#r) r

• `get` **r**(): `number`

#### [#](#Returns-7) Returns

`number`

• `set` **r**(`val`): `void`

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `val` | `number` |

#### [#](#Returns-8) Returns

`void`

---

### [#](#BLACK) BLACK

• `Static` `get` **BLACK**(): [`Color`](./Color.html)

#### [#](#Returns-9) Returns

[`Color`](./Color.html)

---

### [#](#TRANSPARENT) TRANSPARENT

• `Static` `get` **TRANSPARENT**(): [`Color`](./Color.html)

#### [#](#Returns-10) Returns

[`Color`](./Color.html)

---

### [#](#WHITE) WHITE

• `Static` `get` **WHITE**(): [`Color`](./Color.html)

#### [#](#Returns-11) Returns

[`Color`](./Color.html)

## [#](#Methods-2) Methods

### [#](#clone) clone

▸ **clone**(): [`Color`](./Color.html)

#### [#](#Returns-12) Returns

[`Color`](./Color.html)

---

### [#](#equals) equals

▸ **equals**(`target`): `boolean`

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `target` | [`Color`](./Color.html) |

#### [#](#Returns-13) Returns

`boolean`

---

### [#](#mix) mix

▸ **mix**(`color`, `dst?`): [`Color`](./Color.html)

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `color` | [`Color`](./Color.html) |
| `dst?` | [`Color`](./Color.html) |

#### [#](#Returns-14) Returns

[`Color`](./Color.html)

---

### [#](#set) set

▸ **set**(`val`): `void`

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `val` | [`Color`](./Color.html) |

#### [#](#Returns-15) Returns

`void`

---

### [#](#setRGBA) setRGBA

▸ **setRGBA**(`r`, `g`, `b`, `a`): `void`

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `r` | `number` |
| `g` | `number` |
| `b` | `number` |
| `a` | `number` |

#### [#](#Returns-16) Returns

`void`

---

### [#](#setValue32) setValue32

▸ **setValue32**(`v32`): `void`

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `v32` | `number` |

#### [#](#Returns-17) Returns

`void`

---

### [#](#toNormalizedArray) toNormalizedArray

▸ **toNormalizedArray**(): [`number`, `number`, `number`, `number`]

#### [#](#Returns-18) Returns

[`number`, `number`, `number`, `number`]

---

### [#](#toRGBAString) toRGBAString

▸ **toRGBAString**(): `string`

#### [#](#Returns-19) Returns

`string`

---

### [#](#blendColorHex) blendColorHex

▸ `Static` **blendColorHex**(`colorHexA`, `colorHexB`, `type?`): `number`

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `colorHexA` | `number` |
| `colorHexB` | `number` |
| `type` | `BlendType` |

#### [#](#Returns-20) Returns

`number`

---

### [#](#diffc) diffc

▸ `Static` **diffc**(`v`, `c`, `diff`): `number`

#### [#](#Parameters-12) Parameters

| Name | Type |
| --- | --- |
| `v` | `number` |
| `c` | `number` |
| `diff` | `number` |

#### [#](#Returns-21) Returns

`number`

---

### [#](#fromFloatArray) fromFloatArray

▸ `Static` **fromFloatArray**(`arr`): [`Color`](./Color.html)

#### [#](#Parameters-13) Parameters

| Name | Type |
| --- | --- |
| `arr` | `number`[] |

#### [#](#Returns-22) Returns

[`Color`](./Color.html)

---

### [#](#fromHex) fromHex

▸ `Static` **fromHex**(`hex`): [`Color`](./Color.html)

#### [#](#Parameters-14) Parameters

| Name | Type |
| --- | --- |
| `hex` | `number` |

#### [#](#Returns-23) Returns

[`Color`](./Color.html)

---

### [#](#fromHexString) fromHexString

▸ `Static` **fromHexString**(`hexString`): [`Color`](./Color.html)

#### [#](#Parameters-15) Parameters

| Name | Type |
| --- | --- |
| `hexString` | `string` |

#### [#](#Returns-24) Returns

[`Color`](./Color.html)

---

### [#](#getValue32FromHSVA) getValue32FromHSVA

▸ `Static` **getValue32FromHSVA**(): `void`

#### [#](#Returns-25) Returns

`void`

---

### [#](#getValue32FromRGBA) getValue32FromRGBA

▸ `Static` **getValue32FromRGBA**(`r`, `g`, `b`, `a`): `number`

#### [#](#Parameters-16) Parameters

| Name | Type |
| --- | --- |
| `r` | `number` |
| `g` | `number` |
| `b` | `number` |
| `a` | `number` |

#### [#](#Returns-26) Returns

`number`

---

### [#](#hsvV2rgb) hsvV2rgb

▸ `Static` **hsvV2rgb**(`h`, `s`, `v`, `dst?`): [`Vector3`](./Vector3.html)

#### [#](#Parameters-17) Parameters

| Name | Type |
| --- | --- |
| `h` | `number` |
| `s` | `number` |
| `v` | `number` |
| `dst?` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-27) Returns

[`Vector3`](./Vector3.html)

---

### [#](#multiplyColorHex) multiplyColorHex

▸ `Static` **multiplyColorHex**(`colorHexA`, `colorHexB`, `type?`): `number`

#### [#](#Parameters-18) Parameters

| Name | Type |
| --- | --- |
| `colorHexA` | `number` |
| `colorHexB` | `number` |
| `type` | `BlendType` |

#### [#](#Returns-28) Returns

`number`

---

### [#](#percentRoundFn) percentRoundFn

▸ `Static` **percentRoundFn**(`num`): `number`

#### [#](#Parameters-19) Parameters

| Name | Type |
| --- | --- |
| `num` | `number` |

#### [#](#Returns-29) Returns

`number`

---

### [#](#randomMix) randomMix

▸ `Static` **randomMix**(`colorHexA`, `colorHexB`, `randomSeed?`): `number`

#### [#](#Parameters-20) Parameters

| Name | Type |
| --- | --- |
| `colorHexA` | `number` |
| `colorHexB` | `number` |
| `randomSeed` | `number` |

#### [#](#Returns-30) Returns

`number`

---

### [#](#rgb2hsv) rgb2hsv

▸ `Static` **rgb2hsv**(`r`, `g`, `b`, `dst?`): [`Vector3`](./Vector3.html)

#### [#](#Parameters-21) Parameters

| Name | Type |
| --- | --- |
| `r` | `number` |
| `g` | `number` |
| `b` | `number` |
| `dst?` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-31) Returns

[`Vector3`](./Vector3.html)

Incorrect translation.