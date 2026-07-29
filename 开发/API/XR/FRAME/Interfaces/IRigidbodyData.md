[xr-frame](./../) / [Exports](./../modules.html) / IRigidbodyData

# [#](#Interface-IRigidbodyData) Interface: IRigidbodyData

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [constraintsMask](./IRigidbodyData.html#constraintsMask)
- [disabled](./IRigidbodyData.html#disabled)
- [kinematic](./IRigidbodyData.html#kinematic)
- [mass](./IRigidbodyData.html#mass)
- [useGravity](./IRigidbodyData.html#useGravity)

## [#](#Properties-2) Properties

### [#](#constraintsMask) constraintsMask

• `Optional` **constraintsMask**: `number`

限制刚体在某个轴上的位移和旋转。
具体值参考{@link RigidbodyConstraints}

---

### [#](#disabled) disabled

• `Optional` **disabled**: `boolean`

是否禁用刚体。

**`default`** false

---

### [#](#kinematic) kinematic

• `Optional` **kinematic**: `boolean`

是否为*运动学(Kinematic)* 刚体。
设置为*运动学*刚体后，除非手动调用[movePosition](./../classes/Rigidbody.html#movePosition)，否则物体不会在*物理模拟*阶段发生位移或旋转。可以理解为，刚体的行为完全在用户的控制之下。

**`default`** false

---

### [#](#mass) mass

• `Optional` **mass**: `number`

物体的质量。

**`limit`** mass > 0

**`default`** 1

---

### [#](#useGravity) useGravity

• `Optional` **useGravity**: `boolean`

刚体是否受重力影响。

**`default`** true

Incorrect translation.