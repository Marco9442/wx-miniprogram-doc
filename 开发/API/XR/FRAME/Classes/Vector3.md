[xr-frame](./../) / [Exports](./../modules.html) / Vector3

# [#](#Class-Vector3) Class: Vector3

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Vector3.html#constructor)

### [#](#Properties) Properties

- [ForwardLH](./Vector3.html#ForwardLH)
- [ONE](./Vector3.html#ONE)
- [Phys3D](./Vector3.html#Phys3D)
- [Up](./Vector3.html#Up)
- [ZERO](./Vector3.html#ZERO)

### [#](#Accessors) Accessors

- [x](./Vector3.html#x)
- [y](./Vector3.html#y)
- [z](./Vector3.html#z)

### [#](#Methods) Methods

- [abs](./Vector3.html#abs)
- [add](./Vector3.html#add)
- [angleTo](./Vector3.html#angleTo)
- [applyMatrix4](./Vector3.html#applyMatrix4)
- [applyMatrix4Raw](./Vector3.html#applyMatrix4Raw)
- [applyQuaternion](./Vector3.html#applyQuaternion)
- [clone](./Vector3.html#clone)
- [cross](./Vector3.html#cross)
- [distanceTo](./Vector3.html#distanceTo)
- [dot](./Vector3.html#dot)
- [equal](./Vector3.html#equal)
- [fromArray](./Vector3.html#fromArray)
- [fromPhysics](./Vector3.html#fromPhysics)
- [get](./Vector3.html#get)
- [isZero](./Vector3.html#isZero)
- [length](./Vector3.html#length)
- [lerp](./Vector3.html#lerp)
- [negate](./Vector3.html#negate)
- [normalize](./Vector3.html#normalize)
- [print](./Vector3.html#print)
- [scale](./Vector3.html#scale)
- [scaleXYZ](./Vector3.html#scaleXYZ)
- [set](./Vector3.html#set)
- [setArray](./Vector3.html#setArray)
- [setFromArray](./Vector3.html#setFromArray)
- [setFromMatrixColumn](./Vector3.html#setFromMatrixColumn)
- [setFromMatrixPosition](./Vector3.html#setFromMatrixPosition)
- [setFromMatrixScale](./Vector3.html#setFromMatrixScale)
- [setValue](./Vector3.html#setValue)
- [sub](./Vector3.html#sub)
- [toArray](./Vector3.html#toArray)
- [toPhysics](./Vector3.html#toPhysics)
- [transformDirection](./Vector3.html#transformDirection)
- [transformDirectionRaw](./Vector3.html#transformDirectionRaw)
- [clearPhysicsPool](./Vector3.html#clearPhysicsPool)
- [createFromArray](./Vector3.html#createFromArray)
- [createFromNumber](./Vector3.html#createFromNumber)
- [createFromTypedArray](./Vector3.html#createFromTypedArray)
- [fromPhysics](./Vector3.html#fromPhysics-1)
- [transformCoordinate](./Vector3.html#transformCoordinate)
- [transformQuat](./Vector3.html#transformQuat)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Vector3**(`raw?`, `offset?`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `raw?` | `Float32Array` |
| `offset?` | `number` |

## [#](#Properties-2) Properties

### [#](#ForwardLH) ForwardLH

▪ `Static` `Readonly` **ForwardLH**: [`Vector3`](./Vector3.html)

前方向，基于左手坐标系，不要对该对象进行修改

**`static`**

**`memberof`** Vector3

---

### [#](#ONE) ONE

▪ `Static` `Readonly` **ONE**: [`Vector3`](./Vector3.html)

一向量，不要对该对象进行修改

**`readonly`**

**`static`**

**`memberof`** Vector3

---

### [#](#Phys3D) Phys3D

▪ `Static` `Optional` **Phys3D**: typeof `phys3D`

---

### [#](#Up) Up

▪ `Static` `Readonly` **Up**: [`Vector3`](./Vector3.html)

上方向，不要对该对象进行修改

**`static`**

**`memberof`** Vector3

---

### [#](#ZERO) ZERO

▪ `Static` `Readonly` **ZERO**: [`Vector3`](./Vector3.html)

零向量，不要对该对象进行修改

**`readonly`**

**`static`**

**`memberof`** Vector3

## [#](#Accessors-2) Accessors

### [#](#x) x

• `get` **x**(): `number`

x值

**`memberof`** Vector3

#### [#](#Returns) Returns

`number`

• `set` **x**(`val`): `void`

x值

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `val` | `number` |

#### [#](#Returns-2) Returns

`void`

---

### [#](#y) y

• `get` **y**(): `number`

y值

**`memberof`** Vector3

#### [#](#Returns-3) Returns

`number`

• `set` **y**(`val`): `void`

y值

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `val` | `number` |

#### [#](#Returns-4) Returns

`void`

---

### [#](#z) z

• `get` **z**(): `number`

z值

**`memberof`** Vector3

#### [#](#Returns-5) Returns

`number`

• `set` **z**(`val`): `void`

z值

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `val` | `number` |

#### [#](#Returns-6) Returns

`void`

## [#](#Methods-2) Methods

### [#](#abs) abs

▸ **abs**(): [`Vector3`](./Vector3.html)

#### [#](#Returns-7) Returns

[`Vector3`](./Vector3.html)

---

### [#](#add) add

▸ **add**(`v`, `dst?`): [`Vector3`](./Vector3.html)

向量加法

**`memberof`** Vector3

#### [#](#Parameters-5) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector3`](./Vector3.html) | 目标向量 |
| `dst?` | [`Vector3`](./Vector3.html) | - |

#### [#](#Returns-8) Returns

[`Vector3`](./Vector3.html)

计算结果

---

### [#](#angleTo) angleTo

▸ **angleTo**(`location`, `dst?`): [`Vector3`](./Vector3.html)

获取到目标点的角度

**`memberof`** Vector3

#### [#](#Parameters-6) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `location` | [`Vector3`](./Vector3.html) | 目标点 |
| `dst?` | [`Vector3`](./Vector3.html) | - |

#### [#](#Returns-9) Returns

[`Vector3`](./Vector3.html)

计算结果

---

### [#](#applyMatrix4) applyMatrix4

▸ **applyMatrix4**(`m`): [`Vector3`](./Vector3.html)

create by janzen
Multiplies this vector (with an implicit 1 in the 4th dimension) and m, and divides by perspective.

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `m` | [`Matrix4`](./Matrix4.html) |

#### [#](#Returns-10) Returns

[`Vector3`](./Vector3.html)

---

### [#](#applyMatrix4Raw) applyMatrix4Raw

▸ **applyMatrix4Raw**(`m`): [`Vector3`](./Vector3.html)

create by roamye
Multiplies this vector (with an implicit 1 in the 4th dimension) and m, and divides by perspective.

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `m` | `Float32Array` |

#### [#](#Returns-11) Returns

[`Vector3`](./Vector3.html)

---

### [#](#applyQuaternion) applyQuaternion

▸ **applyQuaternion**(`q`): [`Vector3`](./Vector3.html)

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `q` | [`Quaternion`](./Quaternion.html) |

#### [#](#Returns-12) Returns

[`Vector3`](./Vector3.html)

---

### [#](#clone) clone

▸ **clone**(): [`Vector3`](./Vector3.html)

拷贝该向量

**`memberof`** Vector3

#### [#](#Returns-13) Returns

[`Vector3`](./Vector3.html)

拷贝出来的对象

---

### [#](#cross) cross

▸ **cross**(`v`, `dst?`): [`Vector3`](./Vector3.html)

向量叉乘

**`memberof`** Vector3

#### [#](#Parameters-10) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector3`](./Vector3.html) | 目标向量 |
| `dst?` | [`Vector3`](./Vector3.html) | - |

#### [#](#Returns-14) Returns

[`Vector3`](./Vector3.html)

计算结果

---

### [#](#distanceTo) distanceTo

▸ **distanceTo**(`p`): `number`

获取到目标点的距离

**`memberof`** Vector3

#### [#](#Parameters-11) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `p` | [`Vector3`](./Vector3.html) | 目标点 |

#### [#](#Returns-15) Returns

`number`

计算结果

---

### [#](#dot) dot

▸ **dot**(`v`): `number`

向量点乘

**`memberof`** Vector3

#### [#](#Parameters-12) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector3`](./Vector3.html) | 目标向量 |

#### [#](#Returns-16) Returns

`number`

计算结果

---

### [#](#equal) equal

▸ **equal**(`v`): `boolean`

判断与目标向量的值是否相等

**`memberof`** Vector3

#### [#](#Parameters-13) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector3`](./Vector3.html) | 目标向量 |

#### [#](#Returns-17) Returns

`boolean`

是否相等，这里误差小于10^-6视为相等

---

### [#](#fromArray) fromArray

▸ **fromArray**(`array`, `offset`): [`Vector3`](./Vector3.html)

#### [#](#Parameters-14) Parameters

| Name | Type |
| --- | --- |
| `array` | `Float32Array` |
| `offset` | `number` |

#### [#](#Returns-18) Returns

[`Vector3`](./Vector3.html)

---

### [#](#fromPhysics) fromPhysics

▸ **fromPhysics**(`v`): [`Vector3`](./Vector3.html)

#### [#](#Parameters-15) Parameters

| Name | Type |
| --- | --- |
| `v` | `any` |

#### [#](#Returns-19) Returns

[`Vector3`](./Vector3.html)

---

### [#](#get) get

▸ **get**(`i`): `number`

#### [#](#Parameters-16) Parameters

| Name | Type |
| --- | --- |
| `i` | `number` |

#### [#](#Returns-20) Returns

`number`

---

### [#](#isZero) isZero

▸ **isZero**(): `boolean`

是否为零向量

**`memberof`** Vector3

#### [#](#Returns-21) Returns

`boolean`

---

### [#](#length) length

▸ **length**(): `number`

向量的模

**`memberof`** Vector3

#### [#](#Returns-22) Returns

`number`

计算结果

---

### [#](#lerp) lerp

▸ **lerp**(`v`, `f`, `dst?`): [`Vector3`](./Vector3.html)

在该向量与目标向量之间计算插值

**`memberof`** Vector3

#### [#](#Parameters-17) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector3`](./Vector3.html) | 目标向量 |
| `f` | `number` | 插值系数 |
| `dst?` | [`Vector3`](./Vector3.html) | - |

#### [#](#Returns-23) Returns

[`Vector3`](./Vector3.html)

计算结果

---

### [#](#negate) negate

▸ **negate**(): [`Vector3`](./Vector3.html)

取反

#### [#](#Returns-24) Returns

[`Vector3`](./Vector3.html)

---

### [#](#normalize) normalize

▸ **normalize**(`dst?`): [`Vector3`](./Vector3.html)

向量归一化

**`memberof`** Vector3

#### [#](#Parameters-18) Parameters

| Name | Type |
| --- | --- |
| `dst?` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-25) Returns

[`Vector3`](./Vector3.html)

计算结果

---

### [#](#print) print

▸ **print**(): `void`

#### [#](#Returns-26) Returns

`void`

---

### [#](#scale) scale

▸ **scale**(`f`, `dst?`): [`Vector3`](./Vector3.html)

向量缩放

**`memberof`** Vector3

#### [#](#Parameters-19) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `f` | `number` | 缩放比 |
| `dst?` | [`Vector3`](./Vector3.html) | - |

#### [#](#Returns-27) Returns

[`Vector3`](./Vector3.html)

计算结果

---

### [#](#scaleXYZ) scaleXYZ

▸ **scaleXYZ**(`x`, `y`, `z`, `dst?`): [`Vector3`](./Vector3.html)

向量缩放

**`memberof`** Vector3

#### [#](#Parameters-20) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `x` | `number` | x缩放比 |
| `y` | `number` | y缩放比 |
| `z` | `number` | z缩放比 |
| `dst?` | [`Vector3`](./Vector3.html) | - |

#### [#](#Returns-28) Returns

[`Vector3`](./Vector3.html)

计算结果

---

### [#](#set) set

▸ **set**(`v`): [`Vector3`](./Vector3.html)

拷贝目标向量的值到该向量

**`memberof`** Vector3

#### [#](#Parameters-21) Parameters

| Name | Type |
| --- | --- |
| `v` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-29) Returns

[`Vector3`](./Vector3.html)

自身

---

### [#](#setArray) setArray

▸ **setArray**(`value`, `offset?`): [`Vector3`](./Vector3.html)

#### [#](#Parameters-22) Parameters

| Name | Type |
| --- | --- |
| `value` | `ArrayLike`<`number`> |
| `offset?` | `number` |

#### [#](#Returns-30) Returns

[`Vector3`](./Vector3.html)

---

### [#](#setFromArray) setFromArray

▸ **setFromArray**(`xyz`): [`Vector3`](./Vector3.html)

#### [#](#Parameters-23) Parameters

| Name | Type |
| --- | --- |
| `xyz` | `number`[] |

#### [#](#Returns-31) Returns

[`Vector3`](./Vector3.html)

---

### [#](#setFromMatrixColumn) setFromMatrixColumn

▸ **setFromMatrixColumn**(`m`, `index`): [`Vector3`](./Vector3.html)

#### [#](#Parameters-24) Parameters

| Name | Type |
| --- | --- |
| `m` | [`Matrix4`](./Matrix4.html) |
| `index` | `number` |

#### [#](#Returns-32) Returns

[`Vector3`](./Vector3.html)

---

### [#](#setFromMatrixPosition) setFromMatrixPosition

▸ **setFromMatrixPosition**(`worldMatrix`): [`Vector3`](./Vector3.html)

create by janzen
Sets this vector to the position elements of the transformation matrix

#### [#](#Parameters-25) Parameters

| Name | Type |
| --- | --- |
| `worldMatrix` | [`Matrix4`](./Matrix4.html) |

#### [#](#Returns-33) Returns

[`Vector3`](./Vector3.html)

---

### [#](#setFromMatrixScale) setFromMatrixScale

▸ **setFromMatrixScale**(`m`): [`Vector3`](./Vector3.html)

#### [#](#Parameters-26) Parameters

| Name | Type |
| --- | --- |
| `m` | [`Matrix4`](./Matrix4.html) |

#### [#](#Returns-34) Returns

[`Vector3`](./Vector3.html)

---

### [#](#setValue) setValue

▸ **setValue**(`x`, `y`, `z`): [`Vector3`](./Vector3.html)

设置向量的值

**`memberof`** Vector3

#### [#](#Parameters-27) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `x` | `number` | x |
| `y` | `number` | y |
| `z` | `number` | z |

#### [#](#Returns-35) Returns

[`Vector3`](./Vector3.html)

自身

---

### [#](#sub) sub

▸ **sub**(`v`, `dst?`): [`Vector3`](./Vector3.html)

向量减法

**`memberof`** Vector3

#### [#](#Parameters-28) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector3`](./Vector3.html) | 目标向量 |
| `dst?` | [`Vector3`](./Vector3.html) | - |

#### [#](#Returns-36) Returns

[`Vector3`](./Vector3.html)

计算结果

---

### [#](#toArray) toArray

▸ **toArray**(): [`number`, `number`, `number`]

返回向量数据

**`memberof`** Vector3

#### [#](#Returns-37) Returns

[`number`, `number`, `number`]

矩阵数据，以JSArray返回

---

### [#](#toPhysics) toPhysics

▸ **toPhysics**(): `any`

created by shanexyzhou
生成物理引擎内的RawVec3f

#### [#](#Returns-38) Returns

`any`

---

### [#](#transformDirection) transformDirection

▸ **transformDirection**(`m`): [`Vector3`](./Vector3.html)

create by janzen
Transforms the direction of this vector by a matrix (the upper left 3 x 3 subset of a m) and then normalizes the result.

#### [#](#Parameters-29) Parameters

| Name | Type |
| --- | --- |
| `m` | [`Matrix4`](./Matrix4.html) |

#### [#](#Returns-39) Returns

[`Vector3`](./Vector3.html)

---

### [#](#transformDirectionRaw) transformDirectionRaw

▸ **transformDirectionRaw**(`raw`): [`Vector3`](./Vector3.html)

create by roamye
Transforms the direction of this vector by a matrix (the upper left 3 x 3 subset of a m) and then normalizes the result.

#### [#](#Parameters-30) Parameters

| Name | Type |
| --- | --- |
| `raw` | `Float32Array` |

#### [#](#Returns-40) Returns

[`Vector3`](./Vector3.html)

---

### [#](#clearPhysicsPool) clearPhysicsPool

▸ `Static` **clearPhysicsPool**(): `void`

#### [#](#Returns-41) Returns

`void`

---

### [#](#createFromArray) createFromArray

▸ `Static` **createFromArray**(`array`): [`Vector3`](./Vector3.html)

使用一个数组创建
此操作会拷贝一份数组

**`static`**

**`memberof`** Vector3

#### [#](#Parameters-31) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `array` | `number`[] | 数据源，长度必须为3，否则会抛出异常 |

#### [#](#Returns-42) Returns

[`Vector3`](./Vector3.html)

创建出来的向量

---

### [#](#createFromNumber) createFromNumber

▸ `Static` **createFromNumber**(`x`, `y`, `z`): [`Vector3`](./Vector3.html)

使用数值创建
推荐使用这种方式代替new Vector3

**`static`**

**`memberof`** Vector3

#### [#](#Parameters-32) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `x` | `number` | x |
| `y` | `number` | y |
| `z` | `number` | z |

#### [#](#Returns-43) Returns

[`Vector3`](./Vector3.html)

创建出来的向量

---

### [#](#createFromTypedArray) createFromTypedArray

▸ `Static` **createFromTypedArray**(`array`, `offset?`): [`Vector3`](./Vector3.html)

使用某个已有的typedArray创建
此操作不会拷贝数据，而是在原来的内存区域上操作

**`static`**

**`memberof`** Vector3

#### [#](#Parameters-33) Parameters

| Name | Type | Default value | Description |
| --- | --- | --- | --- |
| `array` | `Float32Array` | `undefined` | 数据源 |
| `offset` | `number` | `0` | - |

#### [#](#Returns-44) Returns

[`Vector3`](./Vector3.html)

---

### [#](#fromPhysics-2) fromPhysics

▸ `Static` **fromPhysics**(`v`): [`Vector3`](./Vector3.html)

created by shanexyzhou
从物理引擎内的RawVec3f生成Vector3

#### [#](#Parameters-34) Parameters

| Name | Type |
| --- | --- |
| `v` | `any` |

#### [#](#Returns-45) Returns

[`Vector3`](./Vector3.html)

---

### [#](#transformCoordinate) transformCoordinate

▸ `Static` **transformCoordinate**(`coordinate`, `transform`, `dst?`): [`Vector3`](./Vector3.html)

#### [#](#Parameters-35) Parameters

| Name | Type |
| --- | --- |
| `coordinate` | [`Vector3`](./Vector3.html) |
| `transform` | [`Matrix4`](./Matrix4.html) |
| `dst?` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-46) Returns

[`Vector3`](./Vector3.html)

---

### [#](#transformQuat) transformQuat

▸ `Static` **transformQuat**(`source`, `rotation`, `dst?`): [`Vector3`](./Vector3.html)

使用四元数进行向量旋转

**`static`**

**`memberof`** Vector3

#### [#](#Parameters-36) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `source` | [`Vector3`](./Vector3.html) | 源向量 |
| `rotation` | [`Quaternion`](./Quaternion.html) | 用于旋转的四元数 |
| `dst?` | [`Vector3`](./Vector3.html) | - |

#### [#](#Returns-47) Returns

[`Vector3`](./Vector3.html)

计算结果

Incorrect translation.