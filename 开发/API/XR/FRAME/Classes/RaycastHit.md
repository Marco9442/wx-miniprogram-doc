[xr-frame](./../) / [Exports](./../modules.html) / RaycastHit

# [#](#Class-RaycastHit) Class: RaycastHit

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./RaycastHit.html#constructor)

### [#](#Accessors) Accessors

- [distance](./RaycastHit.html#distance)
- [normal](./RaycastHit.html#normal)
- [point](./RaycastHit.html#point)
- [shape](./RaycastHit.html#shape)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new RaycastHit**(`scene`, `nativeComp?`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `scene` | [`Scene`](./Scene.html) |
| `nativeComp?` | `RaycastHit` |

## [#](#Accessors-2) Accessors

### [#](#distance) distance

• `get` **distance**(): `number`

从射线的原点到碰撞点的距离。

#### [#](#Returns) Returns

`number`

• `set` **distance**(`v`): `void`

从射线的原点到碰撞点的距离。

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `v` | `number` |

#### [#](#Returns-2) Returns

`void`

---

### [#](#normal) normal

• `get` **normal**(): [`Vector3`](./Vector3.html)

射线与轮廓的交点表面的法线。

#### [#](#Returns-3) Returns

[`Vector3`](./Vector3.html)

• `set` **normal**(`v`): `void`

射线与轮廓的交点表面的法线。

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `v` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-4) Returns

`void`

---

### [#](#point) point

• `get` **point**(): [`Vector3`](./Vector3.html)

在世界空间中，射线与轮廓的交点。

#### [#](#Returns-5) Returns

[`Vector3`](./Vector3.html)

• `set` **point**(`v`): `void`

在世界空间中，射线与轮廓的交点。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `v` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-6) Returns

`void`

---

### [#](#shape) shape

• `get` **shape**(): [`Shape`](./Shape.html)<`any`>

与射线相交的Shape。

#### [#](#Returns-7) Returns

[`Shape`](./Shape.html)<`any`>

Incorrect translation.