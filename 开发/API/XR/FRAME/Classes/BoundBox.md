[xr-frame](./../) / [Exports](./../modules.html) / BoundBox

# [#](#Class-BoundBox) Class: BoundBox

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./BoundBox.html#constructor)

### [#](#Properties) Properties

- [OFFSETS](./BoundBox.html#OFFSETS)

### [#](#Accessors) Accessors

- [center](./BoundBox.html#center)
- [size](./BoundBox.html#size)

### [#](#Methods) Methods

- [addPoint](./BoundBox.html#addPoint)
- [endInitByPoints](./BoundBox.html#endInitByPoints)
- [initByPoints](./BoundBox.html#initByPoints)
- [setValue](./BoundBox.html#setValue)
- [startInitByPoints](./BoundBox.html#startInitByPoints)
- [createFromCenterAndSize](./BoundBox.html#createFromCenterAndSize)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new BoundBox**(`raw?`, `offset?`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `raw?` | `Float32Array` |
| `offset?` | `number` |

## [#](#Properties-2) Properties

### [#](#OFFSETS) OFFSETS

▪ `Static` `Readonly` **OFFSETS**: `Readonly`<{ `center`: `number` = 0; `size`: `number` = 3 }>

## [#](#Accessors-2) Accessors

### [#](#center) center

• `get` **center**(): [`Vector3`](./Vector3.html)

包围盒中心

**`memberof`** BoundBox

#### [#](#Returns) Returns

[`Vector3`](./Vector3.html)

• `set` **center**(`val`): `void`

包围盒中心

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `val` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-2) Returns

`void`

---

### [#](#size) size

• `get` **size**(): [`Vector3`](./Vector3.html)

包围盒尺寸

**`memberof`** BoundBox

#### [#](#Returns-3) Returns

[`Vector3`](./Vector3.html)

• `set` **size**(`val`): `void`

包围盒尺寸

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `val` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-4) Returns

`void`

## [#](#Methods-2) Methods

### [#](#addPoint) addPoint

▸ **addPoint**(`corner`): `void`

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `corner` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-5) Returns

`void`

---

### [#](#endInitByPoints) endInitByPoints

▸ **endInitByPoints**(): `void`

#### [#](#Returns-6) Returns

`void`

---

### [#](#initByPoints) initByPoints

▸ **initByPoints**(`points`, `length?`): `void`

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `points` | [`Vector3`](./Vector3.html)[] |
| `length?` | `number` |

#### [#](#Returns-7) Returns

`void`

---

### [#](#setValue) setValue

▸ **setValue**(`center`, `size`): [`BoundBox`](./BoundBox.html)

设置值

**`memberof`** BoundBox

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `center` | [`Vector3`](./Vector3.html) |
| `size` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-8) Returns

[`BoundBox`](./BoundBox.html)

---

### [#](#startInitByPoints) startInitByPoints

▸ **startInitByPoints**(): `void`

#### [#](#Returns-9) Returns

`void`

---

### [#](#createFromCenterAndSize) createFromCenterAndSize

▸ `Static` **createFromCenterAndSize**(`center`, `size`): [`BoundBox`](./BoundBox.html)

使用中心和尺寸创建包围球

**`static`**

**`memberof`** BoundBall

#### [#](#Parameters-7) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `center` | [`Vector3`](./Vector3.html) | 中心 |
| `size` | [`Vector3`](./Vector3.html) | 尺寸 |

#### [#](#Returns-10) Returns

[`BoundBox`](./BoundBox.html)

Incorrect translation.