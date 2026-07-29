[xr-frame](./../) / [Exports](./../modules.html) / ICollideEvent

# [#](#Interface-ICollideEvent) Interface: ICollideEvent

物理碰撞事件（collide-begin等）的信息。

**`readonly`**

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [contacts](./ICollideEvent.html#contacts)
- [impulse](./ICollideEvent.html#impulse)
- [relativeVelocity](./ICollideEvent.html#relativeVelocity)
- [shape](./ICollideEvent.html#shape)

## [#](#Properties-2) Properties

### [#](#contacts) contacts

• `Readonly` **contacts**: [`IContactPoint`](./IContactPoint.html)[]

本次碰撞的接触点。

---

### [#](#impulse) impulse

• `Readonly` **impulse**: `Vector3_READONLY`

从碰撞到分离所用的冲量之和。

---

### [#](#relativeVelocity) relativeVelocity

• `Readonly` **relativeVelocity**: `Vector3_READONLY`

两个刚体的相对线性碰撞速度。

---

### [#](#shape) shape

• `Readonly` **shape**: [`Shape`](./../classes/Shape.html)<`any`>

发生碰撞的另一个轮廓。

Incorrect translation.