[xr-frame](./../) / [Exports](./../modules.html) / Quaternion

# [#](#Class-Quaternion) Class: Quaternion

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Quaternion.html#constructor)

### [#](#Properties) Properties

- [DEFAULT](./Quaternion.html#DEFAULT)
- [Phys3D](./Quaternion.html#Phys3D)

### [#](#Accessors) Accessors

- [w](./Quaternion.html#w)
- [x](./Quaternion.html#x)
- [y](./Quaternion.html#y)
- [z](./Quaternion.html#z)

### [#](#Methods) Methods

- [add](./Quaternion.html#add)
- [angleTo](./Quaternion.html#angleTo)
- [clone](./Quaternion.html#clone)
- [dot](./Quaternion.html#dot)
- [equal](./Quaternion.html#equal)
- [fromPhysics](./Quaternion.html#fromPhysics)
- [invert](./Quaternion.html#invert)
- [isDefault](./Quaternion.html#isDefault)
- [length](./Quaternion.html#length)
- [multiply](./Quaternion.html#multiply)
- [normalize](./Quaternion.html#normalize)
- [premultiply](./Quaternion.html#premultiply)
- [rotateTowards](./Quaternion.html#rotateTowards)
- [set](./Quaternion.html#set)
- [setArray](./Quaternion.html#setArray)
- [setFromEulerAngles](./Quaternion.html#setFromEulerAngles)
- [setFromUnitVectors](./Quaternion.html#setFromUnitVectors)
- [setFromYawRollPitch](./Quaternion.html#setFromYawRollPitch)
- [setValue](./Quaternion.html#setValue)
- [slerp](./Quaternion.html#slerp)
- [sub](./Quaternion.html#sub)
- [toAxisUnit](./Quaternion.html#toAxisUnit)
- [toEulerAngles](./Quaternion.html#toEulerAngles)
- [toPhysics](./Quaternion.html#toPhysics)
- [transformVector3](./Quaternion.html#transformVector3)
- [clearPhysicsPool](./Quaternion.html#clearPhysicsPool)
- [createFromArray](./Quaternion.html#createFromArray)
- [createFromAxisAngle](./Quaternion.html#createFromAxisAngle)
- [createFromMatrix4](./Quaternion.html#createFromMatrix4)
- [createFromNumber](./Quaternion.html#createFromNumber)
- [createFromTypedArray](./Quaternion.html#createFromTypedArray)
- [createFromUnitVectors](./Quaternion.html#createFromUnitVectors)
- [fromEulerAngles](./Quaternion.html#fromEulerAngles)
- [fromPhysics](./Quaternion.html#fromPhysics-1)
- [lookRotation](./Quaternion.html#lookRotation)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Quaternion**(`raw?`, `offset?`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `raw?` | `Float32Array` |
| `offset?` | `number` |

## [#](#Properties-2) Properties

### [#](#DEFAULT) DEFAULT

▪ `Static` `Readonly` **DEFAULT**: [`Quaternion`](./Quaternion.html)

默认四元数，不要对该对象进行修改

**`readonly`**

**`static`**

**`memberof`** Quaternion

---

### [#](#Phys3D) Phys3D

▪ `Static` `Optional` **Phys3D**: typeof `phys3D`

## [#](#Accessors-2) Accessors

### [#](#w) w

• `get` **w**(): `number`

w值

**`memberof`** Quaternion

#### [#](#Returns) Returns

`number`

• `set` **w**(`val`): `void`

w值

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `val` | `number` |

#### [#](#Returns-2) Returns

`void`

---

### [#](#x) x

• `get` **x**(): `number`

x值

**`memberof`** Quaternion

#### [#](#Returns-3) Returns

`number`

• `set` **x**(`val`): `void`

x值

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `val` | `number` |

#### [#](#Returns-4) Returns

`void`

---

### [#](#y) y

• `get` **y**(): `number`

y值

**`memberof`** Quaternion

#### [#](#Returns-5) Returns

`number`

• `set` **y**(`val`): `void`

y值

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `val` | `number` |

#### [#](#Returns-6) Returns

`void`

---

### [#](#z) z

• `get` **z**(): `number`

z值

**`memberof`** Quaternion

#### [#](#Returns-7) Returns

`number`

• `set` **z**(`val`): `void`

z值

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `val` | `number` |

#### [#](#Returns-8) Returns

`void`

## [#](#Methods-2) Methods

### [#](#add) add

▸ **add**(`quat`, `dst?`): [`Quaternion`](./Quaternion.html)

四元数相加

**`memberof`** Quaternion

#### [#](#Parameters-6) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `quat` | [`Quaternion`](./Quaternion.html) | 目标四元数 |
| `dst?` | [`Quaternion`](./Quaternion.html) | - |

#### [#](#Returns-9) Returns

[`Quaternion`](./Quaternion.html)

计算结果

---

### [#](#angleTo) angleTo

▸ **angleTo**(`q`): `number`

相对角度

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `q` | [`Quaternion`](./Quaternion.html) |

#### [#](#Returns-10) Returns

`number`

---

### [#](#clone) clone

▸ **clone**(): [`Quaternion`](./Quaternion.html)

拷贝四元数

**`memberof`** Quaternion

#### [#](#Returns-11) Returns

[`Quaternion`](./Quaternion.html)

拷贝后的对象

---

### [#](#dot) dot

▸ **dot**(`q`): `number`

点乘

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `q` | [`Quaternion`](./Quaternion.html) |

#### [#](#Returns-12) Returns

`number`

---

### [#](#equal) equal

▸ **equal**(`quat`): `boolean`

判断与目标四元数的值是否相等

**`memberof`** Quaternion

#### [#](#Parameters-9) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `quat` | [`Quaternion`](./Quaternion.html) | 目标四元数 |

#### [#](#Returns-13) Returns

`boolean`

---

### [#](#fromPhysics) fromPhysics

▸ **fromPhysics**(`v`): [`Quaternion`](./Quaternion.html)

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `v` | `RawQuaternion` |

#### [#](#Returns-14) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#invert) invert

▸ **invert**(`dst?`): [`Quaternion`](./Quaternion.html)

四元数反转

**`memberof`** Quaternion

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `dst?` | [`Quaternion`](./Quaternion.html) |

#### [#](#Returns-15) Returns

[`Quaternion`](./Quaternion.html)

计算结果

---

### [#](#isDefault) isDefault

▸ **isDefault**(): `boolean`

四元数是否为默认四元数（表示零旋转）

**`memberof`** Quaternion

#### [#](#Returns-16) Returns

`boolean`

---

### [#](#length) length

▸ **length**(): `number`

#### [#](#Returns-17) Returns

`number`

---

### [#](#multiply) multiply

▸ **multiply**(`quat`, `dst?`): [`Quaternion`](./Quaternion.html)

四元数相乘

**`memberof`** Quaternion

#### [#](#Parameters-12) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `quat` | [`Quaternion`](./Quaternion.html) | 目标四元数 |
| `dst?` | [`Quaternion`](./Quaternion.html) | - |

#### [#](#Returns-18) Returns

[`Quaternion`](./Quaternion.html)

计算结果

---

### [#](#normalize) normalize

▸ **normalize**(): [`Quaternion`](./Quaternion.html)

#### [#](#Returns-19) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#premultiply) premultiply

▸ **premultiply**(`q`): [`Quaternion`](./Quaternion.html)

#### [#](#Parameters-13) Parameters

| Name | Type |
| --- | --- |
| `q` | [`Quaternion`](./Quaternion.html) |

#### [#](#Returns-20) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#rotateTowards) rotateTowards

▸ **rotateTowards**(`q`, `step`): [`Quaternion`](./Quaternion.html)

转向对应的角度

#### [#](#Parameters-14) Parameters

| Name | Type |
| --- | --- |
| `q` | `any` |
| `step` | `any` |

#### [#](#Returns-21) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#set) set

▸ **set**(`quat`): [`Quaternion`](./Quaternion.html)

拷贝目标四元数的值到自身

**`memberof`** Quaternion

#### [#](#Parameters-15) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `quat` | [`Quaternion`](./Quaternion.html) | 目标四元数 |

#### [#](#Returns-22) Returns

[`Quaternion`](./Quaternion.html)

自身

---

### [#](#setArray) setArray

▸ **setArray**(`value`, `offset?`): [`Quaternion`](./Quaternion.html)

#### [#](#Parameters-16) Parameters

| Name | Type |
| --- | --- |
| `value` | `ArrayLike`<`number`> |
| `offset?` | `number` |

#### [#](#Returns-23) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#setFromEulerAngles) setFromEulerAngles

▸ **setFromEulerAngles**(`euler`): `void`

#### [#](#Parameters-17) Parameters

| Name | Type |
| --- | --- |
| `euler` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-24) Returns

`void`

---

### [#](#setFromUnitVectors) setFromUnitVectors

▸ **setFromUnitVectors**(`vFrom`, `vTo`): [`Quaternion`](./Quaternion.html)

#### [#](#Parameters-18) Parameters

| Name | Type |
| --- | --- |
| `vFrom` | `any` |
| `vTo` | `any` |

#### [#](#Returns-25) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#setFromYawRollPitch) setFromYawRollPitch

▸ **setFromYawRollPitch**(`yaw`, `roll`, `pitch`): `void`

#### [#](#Parameters-19) Parameters

| Name | Type |
| --- | --- |
| `yaw` | `number` |
| `roll` | `number` |
| `pitch` | `number` |

#### [#](#Returns-26) Returns

`void`

---

### [#](#setValue) setValue

▸ **setValue**(`x`, `y`, `z`, `w`): [`Quaternion`](./Quaternion.html)

设置四元数的值

**`memberof`** Quaternion

#### [#](#Parameters-20) Parameters

| Name | Type |
| --- | --- |
| `x` | `number` |
| `y` | `number` |
| `z` | `number` |
| `w` | `number` |

#### [#](#Returns-27) Returns

[`Quaternion`](./Quaternion.html)

自身

---

### [#](#slerp) slerp

▸ **slerp**(`right`, `t`, `dst?`): [`Quaternion`](./Quaternion.html)

球面插值

**`memberof`** Quaternion

#### [#](#Parameters-21) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `right` | [`Quaternion`](./Quaternion.html) | 目标四元数 |
| `t` | `number` | 插值系数，越接近 1 则结果越接近目标 |
| `dst?` | [`Quaternion`](./Quaternion.html) | - |

#### [#](#Returns-28) Returns

[`Quaternion`](./Quaternion.html)

计算结果

---

### [#](#sub) sub

▸ **sub**(`quat`, `dst?`): [`Quaternion`](./Quaternion.html)

四元数相减

**`memberof`** Quaternion

#### [#](#Parameters-22) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `quat` | [`Quaternion`](./Quaternion.html) | 目标四元数 |
| `dst?` | [`Quaternion`](./Quaternion.html) | - |

#### [#](#Returns-29) Returns

[`Quaternion`](./Quaternion.html)

计算结果

---

### [#](#toAxisUnit) toAxisUnit

▸ **toAxisUnit**(): [`Vector3`](./Vector3.html)

对[1,1,1]向量进行转换。

#### [#](#Returns-30) Returns

[`Vector3`](./Vector3.html)

---

### [#](#toEulerAngles) toEulerAngles

▸ **toEulerAngles**(`dst?`): [`Vector3`](./Vector3.html)

将该四元数转换成欧拉角，x代表Pitch,y代表Yaw,z代表Roll
旋转的顺序为YXZ

**`memberof`** Quaternion

#### [#](#Parameters-23) Parameters

| Name | Type |
| --- | --- |
| `dst?` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-31) Returns

[`Vector3`](./Vector3.html)

计算结果

---

### [#](#toPhysics) toPhysics

▸ **toPhysics**(): `RawQuaternion`

created by shanexyzhou
生成物理引擎内的RawQuaternion

#### [#](#Returns-32) Returns

`RawQuaternion`

---

### [#](#transformVector3) transformVector3

▸ **transformVector3**(`vec`): [`Vector3`](./Vector3.html)

#### [#](#Parameters-24) Parameters

| Name | Type |
| --- | --- |
| `vec` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-33) Returns

[`Vector3`](./Vector3.html)

---

### [#](#clearPhysicsPool) clearPhysicsPool

▸ `Static` **clearPhysicsPool**(): `void`

#### [#](#Returns-34) Returns

`void`

---

### [#](#createFromArray) createFromArray

▸ `Static` **createFromArray**(`array`): [`Quaternion`](./Quaternion.html)

使用一个数组创建
此操作会拷贝一份数组

**`static`**

**`memberof`** Quaternion

#### [#](#Parameters-25) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `array` | `number`[] | 数据源，长度必须为4，否则会抛出异常 |

#### [#](#Returns-35) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#createFromAxisAngle) createFromAxisAngle

▸ `Static` **createFromAxisAngle**(`axis`, `rad`, `dst?`): [`Quaternion`](./Quaternion.html)

从轴向旋转创建

**`static`**

**`memberof`** Quaternion

#### [#](#Parameters-26) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `axis` | [`Vector3`](./Vector3.html) | 旋转轴 |
| `rad` | `number` | 旋转幅度 |
| `dst?` | [`Quaternion`](./Quaternion.html) | - |

#### [#](#Returns-36) Returns

[`Quaternion`](./Quaternion.html)

计算结果

---

### [#](#createFromMatrix4) createFromMatrix4

▸ `Static` **createFromMatrix4**(`mat`, `dst?`): [`Quaternion`](./Quaternion.html)

从旋转矩阵创建

**`static`**

**`memberof`** Quaternion

#### [#](#Parameters-27) Parameters

| Name | Type |
| --- | --- |
| `mat` | [`Matrix4`](./Matrix4.html) |
| `dst?` | [`Quaternion`](./Quaternion.html) |

#### [#](#Returns-37) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#createFromNumber) createFromNumber

▸ `Static` **createFromNumber**(`x`, `y`, `z`, `w`): [`Quaternion`](./Quaternion.html)

使用数值创建

**`static`**

**`memberof`** Quaternion

#### [#](#Parameters-28) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `x` | `number` | x |
| `y` | `number` | y |
| `z` | `number` | z |
| `w` | `number` | w |

#### [#](#Returns-38) Returns

[`Quaternion`](./Quaternion.html)

创建出来的四元数

---

### [#](#createFromTypedArray) createFromTypedArray

▸ `Static` **createFromTypedArray**(`array`, `offset?`): [`Quaternion`](./Quaternion.html)

使用某个已有的typedArray创建
此操作不会拷贝数据，而是在原来的内存区域上操作

**`static`**

**`memberof`** Quaternion

#### [#](#Parameters-29) Parameters

| Name | Type | Default value | Description |
| --- | --- | --- | --- |
| `array` | `Float32Array` | `undefined` | 数据源 |
| `offset` | `number` | `0` | - |

#### [#](#Returns-39) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#createFromUnitVectors) createFromUnitVectors

▸ `Static` **createFromUnitVectors**(`vFrom`, `vTo`): [`Quaternion`](./Quaternion.html)

通过俩个向量创建四元数

#### [#](#Parameters-30) Parameters

| Name | Type |
| --- | --- |
| `vFrom` | [`Vector3`](./Vector3.html) |
| `vTo` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-40) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#fromEulerAngles) fromEulerAngles

▸ `Static` **fromEulerAngles**(`euler`, `dst?`): [`Quaternion`](./Quaternion.html)

从欧拉角创建四元数

**`static`**

**`memberof`** Quaternion

#### [#](#Parameters-31) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `euler` | [`Vector3`](./Vector3.html) | 欧拉角，x代表pitch，y代表yaw，z代表roll |
| `dst?` | [`Quaternion`](./Quaternion.html) | - |

#### [#](#Returns-41) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#fromPhysics-2) fromPhysics

▸ `Static` **fromPhysics**(`v`): [`Quaternion`](./Quaternion.html)

created by shanexyzhou
从物理引擎内的RawQuaternion生成Quaternion

#### [#](#Parameters-32) Parameters

| Name | Type |
| --- | --- |
| `v` | `RawQuaternion` |

#### [#](#Returns-42) Returns

[`Quaternion`](./Quaternion.html)

---

### [#](#lookRotation) lookRotation

▸ `Static` **lookRotation**(`forward`, `up`, `dst?`): [`Quaternion`](./Quaternion.html)

由视角方向创建四元数

**`static`**

**`memberof`** Quaternion

#### [#](#Parameters-33) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `forward` | [`Vector3`](./Vector3.html) | 前方向 |
| `up` | [`Vector3`](./Vector3.html) | 上方向 |
| `dst?` | [`Quaternion`](./Quaternion.html) | - |

#### [#](#Returns-43) Returns

[`Quaternion`](./Quaternion.html)

计算结果

Incorrect translation.