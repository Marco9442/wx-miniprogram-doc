[xr-frame](./../) / [Exports](./../modules.html) / IContactPoint

# [#](#Interface-IContactPoint) Interface: IContactPoint

物理事件返回的[碰撞信息](./ICollideEvent.html)中的碰撞点。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [normal](./IContactPoint.html#normal)
- [otherShape](./IContactPoint.html#otherShape)
- [point](./IContactPoint.html#point)
- [separation](./IContactPoint.html#separation)
- [thisShape](./IContactPoint.html#thisShape)

## [#](#Properties-2) Properties

### [#](#normal) normal

• `Readonly` **normal**: `Vector3_READONLY`

碰撞平面的法线。

---

### [#](#otherShape) otherShape

• `Readonly` **otherShape**: [`Shape`](./../classes/Shape.html)<`any`>

另一个轮廓。

---

### [#](#point) point

• `Readonly` **point**: `Vector3_READONLY`

碰撞点的位置。

---

### [#](#separation) separation

• `Readonly` **separation**: `number`

在该碰撞点处，两个物体的距离。

不一定是0或小于0，因为只要两个物体的距离小于{@link Collider.contactOffset}之和，就会判定为碰撞。

---

### [#](#thisShape) thisShape

• `Readonly` **thisShape**: [`Shape`](./../classes/Shape.html)<`any`>

接收碰撞事件的轮廓。

Incorrect translation.