[xr-frame](./../) / [Exports](./../modules.html) / Spherical

# [#](#Class-Spherical) Class: Spherical

球面坐标系。

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Spherical.html#constructor)

### [#](#Properties) Properties

- [center](./Spherical.html#center)
- [isSpherical](./Spherical.html#isSpherical)
- [phi](./Spherical.html#phi)
- [radius](./Spherical.html#radius)
- [theta](./Spherical.html#theta)
- [EPS](./Spherical.html#EPS)

### [#](#Methods) Methods

- [clone](./Spherical.html#clone)
- [copy](./Spherical.html#copy)
- [makeSafe](./Spherical.html#makeSafe)
- [set](./Spherical.html#set)
- [setFromCartesianCoords](./Spherical.html#setFromCartesianCoords)
- [setFromVector3](./Spherical.html#setFromVector3)
- [toVector3](./Spherical.html#toVector3)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Spherical**(`radius?`, `phi?`, `theta?`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `radius?` | `number` |
| `phi?` | `number` |
| `theta?` | `number` |

## [#](#Properties-2) Properties

### [#](#center) center

• **center**: [`Vector3`](./Vector3.html)

球面球心。

---

### [#](#isSpherical) isSpherical

• **isSpherical**: `boolean` = `true`

---

### [#](#phi) phi

• **phi**: `number`

点在球面上的横向旋转角度。

---

### [#](#radius) radius

• **radius**: `number`

球面半径。

---

### [#](#theta) theta

• **theta**: `number`

点在球面上的纵向旋转角度。

---

### [#](#EPS) EPS

▪ `Static` **EPS**: `number` = `0.000001`

## [#](#Methods-2) Methods

### [#](#clone) clone

▸ **clone**(): [`Spherical`](./Spherical.html)

#### [#](#Returns) Returns

[`Spherical`](./Spherical.html)

---

### [#](#copy) copy

▸ **copy**(`other`): [`Spherical`](./Spherical.html)

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `other` | [`Spherical`](./Spherical.html) |

#### [#](#Returns-2) Returns

[`Spherical`](./Spherical.html)

---

### [#](#makeSafe) makeSafe

▸ **makeSafe**(): [`Spherical`](./Spherical.html)

restrict phi to be between EPS and PI-EPS。

#### [#](#Returns-3) Returns

[`Spherical`](./Spherical.html)

---

### [#](#set) set

▸ **set**(`radius`, `phi`, `theta`): [`Spherical`](./Spherical.html)

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `radius` | `number` |
| `phi` | `number` |
| `theta` | `number` |

#### [#](#Returns-4) Returns

[`Spherical`](./Spherical.html)

---

### [#](#setFromCartesianCoords) setFromCartesianCoords

▸ **setFromCartesianCoords**(`x`, `y`, `z`): [`Spherical`](./Spherical.html)

从笛卡尔坐标系的x、y、z转换。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `x` | `number` |
| `y` | `number` |
| `z` | `number` |

#### [#](#Returns-5) Returns

[`Spherical`](./Spherical.html)

---

### [#](#setFromVector3) setFromVector3

▸ **setFromVector3**(`vector`): [`Spherical`](./Spherical.html)

从笛卡尔坐标系的Vector3转换。

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `vector` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-6) Returns

[`Spherical`](./Spherical.html)

---

### [#](#toVector3) toVector3

▸ **toVector3**(`vector?`): [`Vector3`](./Vector3.html)

转换到笛卡尔坐标系的Vector3。

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `vector?` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-7) Returns

[`Vector3`](./Vector3.html)

Incorrect translation.