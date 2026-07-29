[xr-frame](./../) / [Exports](./../modules.html) / IShapeInteractData

# [#](#Interface-IShapeInteractData) Interface: IShapeInteractData

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [bounciness](./IShapeInteractData.html#bounciness)
- [collide](./IShapeInteractData.html#collide)
- [disabled](./IShapeInteractData.html#disabled)
- [dynamicFriction](./IShapeInteractData.html#dynamicFriction)
- [staticFriction](./IShapeInteractData.html#staticFriction)

## [#](#Properties-2) Properties

### [#](#bounciness) bounciness

• `Optional` **bounciness**: `number`

弹性系数，决定碰撞时的能量损失比例。

弹性系数 = 1时，碰撞无能量损失。

**`limit`** 0 <= bounciness <= 1

**`default`** 0

---

### [#](#collide) collide

• `Optional` **collide**: `boolean`

是否能与其他Shape发生物理碰撞。

**`default`** false

---

### [#](#disabled) disabled

• `Optional` **disabled**: `boolean`

是否禁用Shape间交互。

**`default`** false

---

### [#](#dynamicFriction) dynamicFriction

• `Optional` **dynamicFriction**: `number`

动摩擦系数。

**`limit`** 0 <= dynamicFriction <= 1

**`default`** 0.6

---

### [#](#staticFriction) staticFriction

• `Optional` **staticFriction**: `number`

静摩擦系数

**`limit`** 0 <= staticFriction <= 1

**`default`** 0.6

Incorrect translation.