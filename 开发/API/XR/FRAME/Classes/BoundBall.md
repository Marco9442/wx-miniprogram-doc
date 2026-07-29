[xr-frame](./../) / [Exports](./../modules.html) / BoundBall

# [#](#Class-BoundBall) Class: BoundBall

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./BoundBall.html#constructor)

### [#](#Properties) Properties

- [OFFSETS](./BoundBall.html#OFFSETS)

### [#](#Accessors) Accessors

- [center](./BoundBall.html#center)
- [radius](./BoundBall.html#radius)

### [#](#Methods) Methods

- [initByPointRadius](./BoundBall.html#initByPointRadius)
- [initByPoints](./BoundBall.html#initByPoints)
- [setValue](./BoundBall.html#setValue)
- [createFromCenterAndRadius](./BoundBall.html#createFromCenterAndRadius)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new BoundBall**(`raw?`, `offset?`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `raw?` | `Float32Array` |
| `offset?` | `number` |

## [#](#Properties-2) Properties

### [#](#OFFSETS) OFFSETS

▪ `Static` `Readonly` **OFFSETS**: `Readonly`<{ `center`: `number` = 0; `radius`: `number` = 3 }>

## [#](#Accessors-2) Accessors

### [#](#center) center

• `get` **center**(): [`Vector3`](./Vector3.html)

包围球中心

**`memberof`** BoundBall

#### [#](#Returns) Returns

[`Vector3`](./Vector3.html)

• `set` **center**(`val`): `void`

包围球中心

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `val` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-2) Returns

`void`

---

### [#](#radius) radius

• `get` **radius**(): `number`

包围球半径

**`memberof`** BoundBall

#### [#](#Returns-3) Returns

`number`

• `set` **radius**(`val`): `void`

包围球半径

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `val` | `number` |

#### [#](#Returns-4) Returns

`void`

## [#](#Methods-2) Methods

### [#](#initByPointRadius) initByPointRadius

▸ **initByPointRadius**(`center`, `radius`): `void`

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `center` | [`Vector3`](./Vector3.html) |
| `radius` | `number` |

#### [#](#Returns-5) Returns

`void`

---

### [#](#initByPoints) initByPoints

▸ **initByPoints**(`points`): [`BoundBall`](./BoundBall.html)

使用一系列点初始化

**`memberof`** BoundBall

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `points` | [`Vector3`](./Vector3.html)[] |

#### [#](#Returns-6) Returns

[`BoundBall`](./BoundBall.html)

自身

---

### [#](#setValue) setValue

▸ **setValue**(`center`, `radius`): [`BoundBall`](./BoundBall.html)

设置值

**`memberof`** BoundBall

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `center` | [`Vector3`](./Vector3.html) |
| `radius` | `number` |

#### [#](#Returns-7) Returns

[`BoundBall`](./BoundBall.html)

---

### [#](#createFromCenterAndRadius) createFromCenterAndRadius

▸ `Static` **createFromCenterAndRadius**(`center`, `radius`): [`BoundBall`](./BoundBall.html)

使用中心和半径创建包围球

**`static`**

**`memberof`** BoundBall

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `center` | [`Vector3`](./Vector3.html) |
| `radius` | `number` |

#### [#](#Returns-8) Returns

[`BoundBall`](./BoundBall.html)

Incorrect translation.