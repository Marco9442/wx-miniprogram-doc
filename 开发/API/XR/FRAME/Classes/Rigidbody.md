[xr-frame](./../) / [Exports](./../modules.html) / Rigidbody

# [#](#Class-Rigidbody) Class: Rigidbody

刚体组件。

让物体在物理系统中成为一个有质量的刚体。只有添加了这个组件之后，物体才有可能在物理系统的*物理模拟*阶段发生位移和旋转。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IRigidbodyData`](./../interfaces/IRigidbodyData.html)>

  ↳ **`Rigidbody`**

## [#](#Table-of-contents) Table of contents

### [#](#Events) Events

- [onAdd](./Rigidbody.html#onAdd)
- [onRelease](./Rigidbody.html#onRelease)
- [onRemove](./Rigidbody.html#onRemove)
- [onTick](./Rigidbody.html#onTick)
- [onUpdate](./Rigidbody.html#onUpdate)

### [#](#Properties) Properties

- [priority](./Rigidbody.html#priority)
- [schema](./Rigidbody.html#schema)
- [EVENTS](./Rigidbody.html#EVENTS)

### [#](#Accessors) Accessors

- [angularDamping](./Rigidbody.html#angularDamping)
- [angularVelocity](./Rigidbody.html#angularVelocity)
- [centerOfMass](./Rigidbody.html#centerOfMass)
- [collisionDetectionMode](./Rigidbody.html#collisionDetectionMode)
- [detectCollisions](./Rigidbody.html#detectCollisions)
- [el](./Rigidbody.html#el)
- [freezeRotation](./Rigidbody.html#freezeRotation)
- [inertiaTensor](./Rigidbody.html#inertiaTensor)
- [isKinematic](./Rigidbody.html#isKinematic)
- [linearDamping](./Rigidbody.html#linearDamping)
- [mass](./Rigidbody.html#mass)
- [maxAngularVelocity](./Rigidbody.html#maxAngularVelocity)
- [maxDepenetrationVelocity](./Rigidbody.html#maxDepenetrationVelocity)
- [position](./Rigidbody.html#position)
- [positionConstraints](./Rigidbody.html#positionConstraints)
- [rotation](./Rigidbody.html#rotation)
- [rotationConstraints](./Rigidbody.html#rotationConstraints)
- [scene](./Rigidbody.html#scene)
- [sleepThreshold](./Rigidbody.html#sleepThreshold)
- [solverIterations](./Rigidbody.html#solverIterations)
- [solverVelocityIterations](./Rigidbody.html#solverVelocityIterations)
- [useGravity](./Rigidbody.html#useGravity)
- [velocity](./Rigidbody.html#velocity)
- [version](./Rigidbody.html#version)

### [#](#Methods) Methods

- [AddExplosionForce](./Rigidbody.html#AddExplosionForce)
- [AddForceAtPosition](./Rigidbody.html#AddForceAtPosition)
- [addForce](./Rigidbody.html#addForce)
- [addRelativeForce](./Rigidbody.html#addRelativeForce)
- [addRelativeTorque](./Rigidbody.html#addRelativeTorque)
- [addTorque](./Rigidbody.html#addTorque)
- [applyData](./Rigidbody.html#applyData)
- [closestPointOnBounds](./Rigidbody.html#closestPointOnBounds)
- [disable](./Rigidbody.html#disable)
- [enable](./Rigidbody.html#enable)
- [getData](./Rigidbody.html#getData)
- [getPointVelocity](./Rigidbody.html#getPointVelocity)
- [getRelativePointVelocity](./Rigidbody.html#getRelativePointVelocity)
- [getWorldCenterOfMass](./Rigidbody.html#getWorldCenterOfMass)
- [isSleeping](./Rigidbody.html#isSleeping)
- [movePosition](./Rigidbody.html#movePosition)
- [moveRotation](./Rigidbody.html#moveRotation)
- [resetCenterOfMass](./Rigidbody.html#resetCenterOfMass)
- [resetInertiaTensor](./Rigidbody.html#resetInertiaTensor)
- [setData](./Rigidbody.html#setData)
- [setDataOne](./Rigidbody.html#setDataOne)
- [setDensity](./Rigidbody.html#setDensity)
- [sleep](./Rigidbody.html#sleep)
- [wakeUp](./Rigidbody.html#wakeUp)

## [#](#Events-2) Events

### [#](#onAdd) onAdd

▸ **onAdd**(`parent`, `data`): `void`

所挂载的`element`被挂载到场景时触发的回调。

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `parent` | [`Element`](./Element.html) |
| `data` | [`IRigidbodyData`](./../interfaces/IRigidbodyData.html) |

#### [#](#Returns) Returns

`void`

#### [#](#Inherited-from) Inherited from

[Component](./Component.html).[onAdd](./Component.html#onAdd)

---

### [#](#onRelease) onRelease

▸ **onRelease**(`data`): `void`

从被挂载的`element`上被移除，或是`element`被销毁时，触发的回调。
一般用于释放持有的资源。

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IRigidbodyData`](./../interfaces/IRigidbodyData.html) |

#### [#](#Returns-2) Returns

`void`

#### [#](#Inherited-from-2) Inherited from

[Component](./Component.html).[onRelease](./Component.html#onRelease)

---

### [#](#onRemove) onRemove

▸ **onRemove**(`parent`, `data`): `void`

所挂载的`element`从父节点`parent`被移除时，或者自己从`element`上被移除时，触发的回调。
一般用于消除功能的运作。
**如果一个组件的元素直接被销毁了，那这个组件就不会经历onRemove而是直接进入onRelease。**

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `parent` | [`Element`](./Element.html) |
| `data` | [`IRigidbodyData`](./../interfaces/IRigidbodyData.html) |

#### [#](#Returns-3) Returns

`void`

#### [#](#Inherited-from-3) Inherited from

[Component](./Component.html).[onRemove](./Component.html#onRemove)

---

### [#](#onTick) onTick

▸ **onTick**(`dateTime`, `data`): `void`

渲染每帧触发的回调。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `dateTime` | `number` |
| `data` | [`IRigidbodyData`](./../interfaces/IRigidbodyData.html) |

#### [#](#Returns-4) Returns

`void`

#### [#](#Inherited-from-4) Inherited from

[Component](./Component.html).[onTick](./Component.html#onTick)

---

### [#](#onUpdate) onUpdate

▸ **onUpdate**(`data`, `preData`): `void`

数据更新时触发的回调。

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IRigidbodyData`](./../interfaces/IRigidbodyData.html) |
| `preData` | [`IRigidbodyData`](./../interfaces/IRigidbodyData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-5) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number` = `401`

自定义组件的更新优先级。

#### [#](#Overrides) Overrides

[Component](./Component.html).[priority](./Component.html#priority)

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html)

自定义组件的`schema`。

#### [#](#Overrides-2) Overrides

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[] = `[]`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[EVENTS](./Component.html#EVENTS)

## [#](#Accessors-2) Accessors

### [#](#angularDamping) angularDamping

• `get` **angularDamping**(): `number`

角速度阻尼。
影响物体的[角速度](./Rigidbody.html#angularVelocity)。

**`limit`** angularDamping >= 0

**`default`** 0.05

#### [#](#Returns-6) Returns

`number`

• `set` **angularDamping**(`v`): `void`

角速度阻尼。
影响物体的[角速度](./Rigidbody.html#angularVelocity)。

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `v` | `number` |

#### [#](#Returns-7) Returns

`void`

---

### [#](#angularVelocity) angularVelocity

• `get` **angularVelocity**(): [`Vector3`](./Vector3.html)

刚体的角速度。

#### [#](#Returns-8) Returns

[`Vector3`](./Vector3.html)

• `set` **angularVelocity**(`v`): `void`

刚体的角速度。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `v` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-9) Returns

`void`

---

### [#](#centerOfMass) centerOfMass

• `get` **centerOfMass**(): [`Vector3`](./Vector3.html)

刚体的质心相对于LocalTransform的偏移量。
如果不手动设置这一项，会自动根据刚体附着的轮廓来计算质心。

**`see`** [resetCenterOfMass](./Rigidbody.html#resetCenterOfMass)

#### [#](#Returns-10) Returns

[`Vector3`](./Vector3.html)

• `set` **centerOfMass**(`v`): `void`

刚体的质心相对于LocalTransform的偏移量。
如果不手动设置这一项，会自动根据刚体附着的轮廓来计算质心。

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `v` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-11) Returns

`void`

---

### [#](#collisionDetectionMode) collisionDetectionMode

• `get` **collisionDetectionMode**(): `CollisionDetectionMode`

设置刚体的碰撞检测模式。
详见{@link CollisionDetectionMode}。

**`default`** {@link CollisionDetectionMode.Discrete}

#### [#](#Returns-12) Returns

`CollisionDetectionMode`

• `set` **collisionDetectionMode**(`v`): `void`

设置刚体的碰撞检测模式。
详见{@link CollisionDetectionMode}。

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `v` | `CollisionDetectionMode` |

#### [#](#Returns-13) Returns

`void`

---

### [#](#detectCollisions) detectCollisions

• `get` **detectCollisions**(): `boolean`

**`unimplemented`**

**`default`** true

#### [#](#Returns-14) Returns

`boolean`

• `set` **detectCollisions**(`v`): `void`

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `v` | `boolean` |

#### [#](#Returns-15) Returns

`void`

---

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-16) Returns

[`Element`](./Element.html)

---

### [#](#freezeRotation) freezeRotation

• `get` **freezeRotation**(): `boolean`

是否允许*物理模拟*过程中对刚体进行旋转。

**`default`** true

#### [#](#Returns-17) Returns

`boolean`

• `set` **freezeRotation**(`v`): `void`

是否允许*物理模拟*过程中对刚体进行旋转。

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `v` | `boolean` |

#### [#](#Returns-18) Returns

`void`

---

### [#](#inertiaTensor) inertiaTensor

• `get` **inertiaTensor**(): `number`

刚体的转动惯量。
如果不手动设置的话，会自动根据刚体上附着的轮廓计算得出。

**`see`** [resetInertiaTensor](./Rigidbody.html#resetInertiaTensor)

#### [#](#Returns-19) Returns

`number`

• `set` **inertiaTensor**(`v`): `void`

刚体的转动惯量。
如果不手动设置的话，会自动根据刚体上附着的轮廓计算得出。

#### [#](#Parameters-12) Parameters

| Name | Type |
| --- | --- |
| `v` | `number` |

#### [#](#Returns-20) Returns

`void`

---

### [#](#isKinematic) isKinematic

• `get` **isKinematic**(): `boolean`

是否为*运动学(Kinematic)* 刚体。
设置为*运动学*刚体后，除非手动调用[movePosition](./Rigidbody.html#movePosition)，否则物体不会在*物理模拟*阶段发生位移或旋转。可以理解为，刚体的行为完全在用户的控制之下。

**`default`** false

#### [#](#Returns-21) Returns

`boolean`

• `set` **isKinematic**(`v`): `void`

是否为*运动学(Kinematic)* 刚体。
设置为*运动学*刚体后，除非手动调用[movePosition](./Rigidbody.html#movePosition)，否则物体不会在*物理模拟*阶段发生位移或旋转。可以理解为，刚体的行为完全在用户的控制之下。

#### [#](#Parameters-13) Parameters

| Name | Type |
| --- | --- |
| `v` | `boolean` |

#### [#](#Returns-22) Returns

`void`

---

### [#](#linearDamping) linearDamping

• `get` **linearDamping**(): `number`

线性阻尼。
影响物体的[线性速度](./Rigidbody.html#velocity)。

**`limit`** linearDamping >= 0

**`default`** 0

#### [#](#Returns-23) Returns

`number`

• `set` **linearDamping**(`v`): `void`

线性阻尼。
影响物体的[线性速度](./Rigidbody.html#velocity)。

#### [#](#Parameters-14) Parameters

| Name | Type |
| --- | --- |
| `v` | `number` |

#### [#](#Returns-24) Returns

`void`

---

### [#](#mass) mass

• `get` **mass**(): `number`

刚体的质量。

**`limit`** mass > 0

**`default`** 1

#### [#](#Returns-25) Returns

`number`

• `set` **mass**(`v`): `void`

刚体的质量。

#### [#](#Parameters-15) Parameters

| Name | Type |
| --- | --- |
| `v` | `number` |

#### [#](#Returns-26) Returns

`void`

---

### [#](#maxAngularVelocity) maxAngularVelocity

• `get` **maxAngularVelocity**(): `number`

最大角速度（弧度）。

**`default`** 7

#### [#](#Returns-27) Returns

`number`

• `set` **maxAngularVelocity**(`v`): `void`

最大角速度（弧度）。

#### [#](#Parameters-16) Parameters

| Name | Type |
| --- | --- |
| `v` | `number` |

#### [#](#Returns-28) Returns

`void`

---

### [#](#maxDepenetrationVelocity) maxDepenetrationVelocity

• `get` **maxDepenetrationVelocity**(): `number`

最大分离速度。
*物理模拟*解决碰撞（相交）的过程中，最大能允许的分离速度。

**`default`** Infinity

#### [#](#Returns-29) Returns

`number`

• `set` **maxDepenetrationVelocity**(`v`): `void`

最大分离速度。
*物理模拟*解决碰撞（相交）的过程中，最大能允许的分离速度。

#### [#](#Parameters-17) Parameters

| Name | Type |
| --- | --- |
| `v` | `number` |

#### [#](#Returns-30) Returns

`void`

---

### [#](#position) position

• `get` **position**(): [`Vector3`](./Vector3.html)

直接获取或修改刚体在*物理系统*中的位置。
物理系统中的位置是独立于Transform组件的。

\**如果你不清楚修改这一项的后果，请不要手动修改它。修改[Transform.position](./Transform.html#position)来代替。*

#### [#](#Returns-31) Returns

[`Vector3`](./Vector3.html)

• `set` **position**(`v`): `void`

直接获取或修改刚体在*物理系统*中的位置。
物理系统中的位置是独立于Transform组件的。

\**如果你不清楚修改这一项的后果，请不要手动修改它。修改[Transform.position](./Transform.html#position)来代替。*

#### [#](#Parameters-18) Parameters

| Name | Type |
| --- | --- |
| `v` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-32) Returns

`void`

---

### [#](#positionConstraints) positionConstraints

• `get` **positionConstraints**(): `boolean`[]

限制物体的位移（X轴，Y轴，Z轴）。

**`default`** [false, false, false]

#### [#](#Returns-33) Returns

`boolean`[]

• `set` **positionConstraints**(`v`): `void`

限制物体的位移（X轴，Y轴，Z轴）。

#### [#](#Parameters-19) Parameters

| Name | Type |
| --- | --- |
| `v` | `boolean`[] |

#### [#](#Returns-34) Returns

`void`

---

### [#](#rotation) rotation

• `get` **rotation**(): [`Quaternion`](./Quaternion.html)

直接获取或修改刚体在*物理系统*中的旋转（以四元数表示）。
物理系统中的旋转是独立于节点系统中的Transform的，详见{@link //TODO}。

\**如果你不清楚修改这一项的后果，请不要手动修改它。修改{@link Transform3D.euler}或{@link Transform3D.quaternion}来代替。*

#### [#](#Returns-35) Returns

[`Quaternion`](./Quaternion.html)

• `set` **rotation**(`v`): `void`

直接获取或修改刚体在*物理系统*中的旋转（以四元数表示）。
物理系统中的旋转是独立于节点系统中的Transform的，详见{@link //TODO}。

\**如果你不清楚修改这一项的后果，请不要手动修改它。修改{@link Transform3D.euler}或{@link Transform3D.quaternion}来代替。*

#### [#](#Parameters-20) Parameters

| Name | Type |
| --- | --- |
| `v` | [`Quaternion`](./Quaternion.html) |

#### [#](#Returns-36) Returns

`void`

---

### [#](#rotationConstraints) rotationConstraints

• `get` **rotationConstraints**(): `boolean`[]

限制物体的旋转（X轴，Y轴，Z轴）。

**`default`** [false, false, false]

#### [#](#Returns-37) Returns

`boolean`[]

• `set` **rotationConstraints**(`v`): `void`

限制物体的旋转（X轴，Y轴，Z轴）。

#### [#](#Parameters-21) Parameters

| Name | Type |
| --- | --- |
| `v` | `boolean`[] |

#### [#](#Returns-38) Returns

`void`

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-39) Returns

[`Scene`](./Scene.html)

---

### [#](#sleepThreshold) sleepThreshold

• `get` **sleepThreshold**(): `number`

设置刚体进入休眠的动能阈值。

**`default`** 0.005

#### [#](#Returns-40) Returns

`number`

• `set` **sleepThreshold**(`v`): `void`

设置刚体进入休眠的动能阈值。

#### [#](#Parameters-22) Parameters

| Name | Type |
| --- | --- |
| `v` | `number` |

#### [#](#Returns-41) Returns

`void`

---

### [#](#solverIterations) solverIterations

• `get` **solverIterations**(): `number`

设置*物理模拟*过程中解决碰撞的迭代次数。
更高的迭代次数，会消耗更多性能，产生更自然的物理碰撞效果。
如果发现静息状态的刚体（比如说放在地面上），会发生抖动，可以考虑提高这项数值。

**`limit`** solverIterations > 0

**`default`** 6

#### [#](#Returns-42) Returns

`number`

• `set` **solverIterations**(`v`): `void`

设置*物理模拟*过程中解决碰撞的迭代次数。
更高的迭代次数，会消耗更多性能，产生更自然的物理碰撞效果。
如果发现静息状态的刚体（比如说放在地面上），会发生抖动，可以考虑提高这项数值。

#### [#](#Parameters-23) Parameters

| Name | Type |
| --- | --- |
| `v` | `number` |

#### [#](#Returns-43) Returns

`void`

---

### [#](#solverVelocityIterations) solverVelocityIterations

• `get` **solverVelocityIterations**(): `number`

设置*物理模拟*过程中计算碰撞后速度的迭代次数。
更高的迭代次数，会消耗更多性能，产生更准确的分离速度。

**`limit`** solverVelocityIterations > 0

**`default`** 1

#### [#](#Returns-44) Returns

`number`

• `set` **solverVelocityIterations**(`v`): `void`

设置*物理模拟*过程中计算碰撞后速度的迭代次数。
更高的迭代次数，会消耗更多性能，产生更准确的分离速度。

#### [#](#Parameters-24) Parameters

| Name | Type |
| --- | --- |
| `v` | `number` |

#### [#](#Returns-45) Returns

`void`

---

### [#](#useGravity) useGravity

• `get` **useGravity**(): `boolean`

刚体是否受重力影响。

**`default`** true

#### [#](#Returns-46) Returns

`boolean`

• `set` **useGravity**(`v`): `void`

刚体是否受重力影响。

#### [#](#Parameters-25) Parameters

| Name | Type |
| --- | --- |
| `v` | `boolean` |

#### [#](#Returns-47) Returns

`void`

---

### [#](#velocity) velocity

• `get` **velocity**(): [`Vector3`](./Vector3.html)

刚体的线性速度。

\**修改这一项会造成速度突变，一般情况下可以使用[addForce](./Rigidbody.html#addForce)来代替。*

#### [#](#Returns-48) Returns

[`Vector3`](./Vector3.html)

• `set` **velocity**(`v`): `void`

刚体的线性速度。

\**修改这一项会造成速度突变，一般情况下可以使用[addForce](./Rigidbody.html#addForce)来代替。*

#### [#](#Parameters-26) Parameters

| Name | Type |
| --- | --- |
| `v` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-49) Returns

`void`

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-50) Returns

`number`

## [#](#Methods-2) Methods

### [#](#AddExplosionForce) AddExplosionForce

▸ **AddExplosionForce**(`explosionForce`, `explosionPosition`, `explosionRadius`, `upwardsModifier`, `mode`): `void`

生成一次模拟爆炸的力。
爆炸范围可以视作一个球状物体，如果球体和刚体产生*相交*，则会在刚体上产生推力。
推力的大小和*相交点*与球心的距离有关，推力的方向从球心指向相交点，推力作用位于*相交点*。

视刚体有无附着的轮廓，分为两种情况：

- 无轮廓（或爆炸球心在刚体轮廓内）
  相交的判定使用刚体的质心；相交点也取刚体的质心。
- 有轮廓
  相交的判定使用刚体的所有轮廓；相交点取轮廓距离球心最近的那一点。

**`limit`** explosionForce > 0

#### [#](#Parameters-27) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `explosionForce` | `number` | 爆炸力的大小。 |
| `explosionPosition` | [`Vector3`](./Vector3.html) | 爆炸球体的球心位置。 |
| `explosionRadius` | `number` | 爆炸球体的半径。 |
| `upwardsModifier` | `number` | 使用相对数值来修改推力的*作用位置*的y坐标。 |
| `mode` | `ForceMode` | 力的类型。 |

#### [#](#Returns-51) Returns

`void`

---

### [#](#AddForceAtPosition) AddForceAtPosition

▸ **AddForceAtPosition**(`force`, `position`, `mode`): `void`

为刚体施加力，会影响刚体的[线性速度](./Rigidbody.html#velocity)和[角速度](./Rigidbody.html#angularVelocity)。

#### [#](#Parameters-28) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `force` | [`Vector3`](./Vector3.html) | 世界坐标下矢量形式的力，作用在position位置上。 |
| `position` | [`Vector3`](./Vector3.html) | 力的作用位置。 |
| `mode` | `ForceMode` | 力的类型。 |

#### [#](#Returns-52) Returns

`void`

---

### [#](#addForce) addForce

▸ **addForce**(`force`, `mode`): `void`

为刚体施加力，会影响刚体的[线性速度](./Rigidbody.html#velocity)。

#### [#](#Parameters-29) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `force` | [`Vector3`](./Vector3.html) | 世界坐标下矢量形式的力，作用在物体质心上。 |
| `mode` | `ForceMode` | 力的类型。 |

#### [#](#Returns-53) Returns

`void`

---

### [#](#addRelativeForce) addRelativeForce

▸ **addRelativeForce**(`force`, `mode`): `void`

为刚体施加力，会影响刚体的[线性速度](./Rigidbody.html#velocity)。

#### [#](#Parameters-30) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `force` | [`Vector3`](./Vector3.html) | **局部**坐标下矢量形式的力，作用在物体质心上。 |
| `mode` | `ForceMode` | 力的类型。 |

#### [#](#Returns-54) Returns

`void`

---

### [#](#addRelativeTorque) addRelativeTorque

▸ **addRelativeTorque**(`torque`, `mode`): `void`

为刚体施加力矩，会影响刚体的[角速度](./Rigidbody.html#angularVelocity)。

#### [#](#Parameters-31) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `torque` | [`Vector3`](./Vector3.html) | **局部**坐标下矢量形式的力矩。 |
| `mode` | `ForceMode` | 力矩的类型。 |

#### [#](#Returns-55) Returns

`void`

---

### [#](#addTorque) addTorque

▸ **addTorque**(`torque`, `mode`): `void`

为刚体施加力矩，会影响刚体的[角速度](./Rigidbody.html#angularVelocity)。

#### [#](#Parameters-32) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `torque` | [`Vector3`](./Vector3.html) | 世界坐标下矢量形式的力矩。 |
| `mode` | `ForceMode` | 力矩的类型。 |

#### [#](#Returns-56) Returns

`void`

---

### [#](#applyData) applyData

▸ **applyData**(`data`): `void`

#### [#](#Parameters-33) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IRigidbodyData`](./../interfaces/IRigidbodyData.html) |

#### [#](#Returns-57) Returns

`void`

---

### [#](#closestPointOnBounds) closestPointOnBounds

▸ **closestPointOnBounds**(`position`): [`Vector3`](./Vector3.html)

测试刚体**表面上**距离某点最近的位置。
如果给予的position在刚体内部，会返回position。
如果刚体无附着的轮廓，会返回[Infinity, Infinity, Infinity]。

#### [#](#Parameters-34) Parameters

| Name | Type |
| --- | --- |
| `position` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-58) Returns

[`Vector3`](./Vector3.html)

---

### [#](#disable) disable

▸ **disable**(): `void`

#### [#](#Returns-59) Returns

`void`

---

### [#](#enable) enable

▸ **enable**(): `void`

#### [#](#Returns-60) Returns

`void`

---

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IRigidbodyData`](./../interfaces/IRigidbodyData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IRigidbodyData`](./../interfaces/IRigidbodyData.html) |

#### [#](#Parameters-35) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-61) Returns

[`IRigidbodyData`](./../interfaces/IRigidbodyData.html)[`T`]

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#getPointVelocity) getPointVelocity

▸ **getPointVelocity**(`worldPoint`): [`Vector3`](./Vector3.html)

获取刚体内某一点在世界坐标下的速度。

#### [#](#Parameters-36) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `worldPoint` | [`Vector3`](./Vector3.html) | 世界坐标下的位置（其实在刚体外也可以）。 |

#### [#](#Returns-62) Returns

[`Vector3`](./Vector3.html)

---

### [#](#getRelativePointVelocity) getRelativePointVelocity

▸ **getRelativePointVelocity**(`relativePoint`): [`Vector3`](./Vector3.html)

获取刚体内某一点在**局部**坐标下的速度。

#### [#](#Parameters-37) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `relativePoint` | [`Vector3`](./Vector3.html) | **局部**坐标下的位置（其实在刚体外也可以）。 |

#### [#](#Returns-63) Returns

[`Vector3`](./Vector3.html)

---

### [#](#getWorldCenterOfMass) getWorldCenterOfMass

▸ **getWorldCenterOfMass**(): [`Vector3`](./Vector3.html)

#### [#](#Returns-64) Returns

[`Vector3`](./Vector3.html)

刚体质心在世界坐标中的位置。

---

### [#](#isSleeping) isSleeping

▸ **isSleeping**(): `boolean`

**`see`** [sleep](./Rigidbody.html#sleep)

#### [#](#Returns-65) Returns

`boolean`

刚体是否处于休眠状态。

---

### [#](#movePosition) movePosition

▸ **movePosition**(`position`): `void`

对于***非**运动学刚体*来说，等于直接修改[position](./Rigidbody.html#position)；
对于*运动学刚体*来说，位置变化会在下一帧生效。可以视作物体在这一帧的*物理模拟*中沿直线路径**移动**到了目的地。

**`see`** [isKinematic](./Rigidbody.html#isKinematic)

#### [#](#Parameters-38) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `position` | [`Vector3`](./Vector3.html) | 位移的终点 |

#### [#](#Returns-66) Returns

`void`

---

### [#](#moveRotation) moveRotation

▸ **moveRotation**(`rotation`): `void`

**`unimplemented`** 暂未支持，请使用[rotation](./Rigidbody.html#rotation)属性或{@link Transform3D.quaternion}代替。

#### [#](#Parameters-39) Parameters

| Name | Type |
| --- | --- |
| `rotation` | [`Quaternion`](./Quaternion.html) |

#### [#](#Returns-67) Returns

`void`

---

### [#](#resetCenterOfMass) resetCenterOfMass

▸ **resetCenterOfMass**(): `void`

手动触发，根据刚体附着的轮廓重新计算刚体的质心。

**`see`** [centerOfMass](./Rigidbody.html#centerOfMass)

#### [#](#Returns-68) Returns

`void`

---

### [#](#resetInertiaTensor) resetInertiaTensor

▸ **resetInertiaTensor**(): `void`

手动触发，根据刚体附着的轮廓重新计算刚体的转动惯量。

**`see`** [inertiaTensor](./Rigidbody.html#inertiaTensor)

#### [#](#Returns-69) Returns

`void`

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-40) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IRigidbodyData`](./../interfaces/IRigidbodyData.html)> |

#### [#](#Returns-70) Returns

`void`

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[setData](./Component.html#setData)

---

### [#](#setDataOne) setDataOne

▸ **setDataOne**<`T`>(`key`, `value`): `void`

设置一个数据。

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IRigidbodyData`](./../interfaces/IRigidbodyData.html) |

#### [#](#Parameters-41) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IRigidbodyData`](./../interfaces/IRigidbodyData.html)[`T`] |

#### [#](#Returns-71) Returns

`void`

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

---

### [#](#setDensity) setDensity

▸ **setDensity**(`density`): `void`

根据给定的密度和刚体附着的轮廓，来计算刚体的质量。

**`see`** [mass](./Rigidbody.html#mass)

#### [#](#Parameters-42) Parameters

| Name | Type |
| --- | --- |
| `density` | `number` |

#### [#](#Returns-72) Returns

`void`

---

### [#](#sleep) sleep

▸ **sleep**(): `void`

强迫刚体进入休眠状态（至少一帧），休眠状态详见{@link //todo}。
\**如果下一帧发生碰撞则会立刻醒来。*

#### [#](#Returns-73) Returns

`void`

---

### [#](#wakeUp) wakeUp

▸ **wakeUp**(): `void`

强制唤醒刚体（离开休眠状态）。

**`see`** [sleep](./Rigidbody.html#sleep)

#### [#](#Returns-74) Returns

`void`

Incorrect translation.