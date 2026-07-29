[xr-frame](./../) / [Exports](./../modules.html) / Vector4

# [#](#Class-Vector4) Class: Vector4

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Vector4.html#constructor)

### [#](#Properties) Properties

- [ONE](./Vector4.html#ONE)
- [ZERO](./Vector4.html#ZERO)

### [#](#Accessors) Accessors

- [w](./Vector4.html#w)
- [x](./Vector4.html#x)
- [y](./Vector4.html#y)
- [z](./Vector4.html#z)

### [#](#Methods) Methods

- [add](./Vector4.html#add)
- [clone](./Vector4.html#clone)
- [dot](./Vector4.html#dot)
- [equal](./Vector4.html#equal)
- [isZero](./Vector4.html#isZero)
- [lerp](./Vector4.html#lerp)
- [negate](./Vector4.html#negate)
- [scale](./Vector4.html#scale)
- [set](./Vector4.html#set)
- [setArray](./Vector4.html#setArray)
- [setValue](./Vector4.html#setValue)
- [sub](./Vector4.html#sub)
- [toArray](./Vector4.html#toArray)
- [createFromArray](./Vector4.html#createFromArray)
- [createFromNumber](./Vector4.html#createFromNumber)
- [createFromTypedArray](./Vector4.html#createFromTypedArray)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Vector4**(`raw?`, `offset?`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `raw?` | `Float32Array` |
| `offset?` | `number` |

## [#](#Properties-2) Properties

### [#](#ONE) ONE

▪ `Static` `Readonly` **ONE**: [`Vector4`](./Vector4.html)

一向量，不要对该对象进行修改

**`readonly`**

**`static`**

**`memberof`** Vector3

---

### [#](#ZERO) ZERO

▪ `Static` `Readonly` **ZERO**: [`Vector4`](./Vector4.html)

零向量，不要对该对象进行修改

**`static`**

**`readonly`**

**`memberof`** Vector4

## [#](#Accessors-2) Accessors

### [#](#w) w

• `get` **w**(): `number`

w值

**`memberof`** Vector4

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

**`memberof`** Vector4

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

**`memberof`** Vector4

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

**`memberof`** Vector4

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

▸ **add**(`v`, `dst?`): [`Vector4`](./Vector4.html)

向量加法

**`memberof`** Vector4

#### [#](#Parameters-6) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector4`](./Vector4.html) | 目标向量 |
| `dst?` | [`Vector4`](./Vector4.html) | - |

#### [#](#Returns-9) Returns

[`Vector4`](./Vector4.html)

计算结果

---

### [#](#clone) clone

▸ **clone**(): [`Vector4`](./Vector4.html)

拷贝该向量

**`memberof`** Vector4

#### [#](#Returns-10) Returns

[`Vector4`](./Vector4.html)

拷贝出来的对象

---

### [#](#dot) dot

▸ **dot**(`v`): `number`

向量点乘

**`memberof`** Vector4

#### [#](#Parameters-7) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector4`](./Vector4.html) | 目标向量 |

#### [#](#Returns-11) Returns

`number`

计算结果

---

### [#](#equal) equal

▸ **equal**(`v`): `boolean`

判断与目标向量的值是否相等

**`memberof`** Vector4

#### [#](#Parameters-8) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector4`](./Vector4.html) | 目标向量 |

#### [#](#Returns-12) Returns

`boolean`

是否相等，这里误差小于10^-6视为相等

---

### [#](#isZero) isZero

▸ **isZero**(): `boolean`

是否为零向量

**`memberof`** Vector4

#### [#](#Returns-13) Returns

`boolean`

---

### [#](#lerp) lerp

▸ **lerp**(`v`, `f`, `dst?`): [`Vector4`](./Vector4.html)

在该向量与目标向量之间计算插值

**`memberof`** Vector4

#### [#](#Parameters-9) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector4`](./Vector4.html) | 目标向量 |
| `f` | `number` | 插值系数 |
| `dst?` | [`Vector4`](./Vector4.html) | - |

#### [#](#Returns-14) Returns

[`Vector4`](./Vector4.html)

计算结果

---

### [#](#negate) negate

▸ **negate**(): [`Vector4`](./Vector4.html)

取反

#### [#](#Returns-15) Returns

[`Vector4`](./Vector4.html)

---

### [#](#scale) scale

▸ **scale**(`f`, `dst?`): [`Vector4`](./Vector4.html)

向量缩放

**`memberof`** Vector4

#### [#](#Parameters-10) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `f` | `number` | 缩放比 |
| `dst?` | [`Vector4`](./Vector4.html) | - |

#### [#](#Returns-16) Returns

[`Vector4`](./Vector4.html)

计算结果

---

### [#](#set) set

▸ **set**(`v`): [`Vector4`](./Vector4.html)

拷贝目标向量的值到该向量

**`memberof`** Vector4

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `v` | [`Vector4`](./Vector4.html) |

#### [#](#Returns-17) Returns

[`Vector4`](./Vector4.html)

自身

---

### [#](#setArray) setArray

▸ **setArray**(`value`, `offset?`): [`Vector4`](./Vector4.html)

#### [#](#Parameters-12) Parameters

| Name | Type |
| --- | --- |
| `value` | `ArrayLike`<`number`> |
| `offset?` | `number` |

#### [#](#Returns-18) Returns

[`Vector4`](./Vector4.html)

---

### [#](#setValue) setValue

▸ **setValue**(`x`, `y`, `z`, `w`): [`Vector4`](./Vector4.html)

设置向量的值

**`memberof`** Vector4

#### [#](#Parameters-13) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `x` | `number` | x值 |
| `y` | `number` | y值 |
| `z` | `number` | z值 |
| `w` | `number` | w值 |

#### [#](#Returns-19) Returns

[`Vector4`](./Vector4.html)

自身

---

### [#](#sub) sub

▸ **sub**(`v`, `dst?`): [`Vector4`](./Vector4.html)

向量减法

**`memberof`** Vector4

#### [#](#Parameters-14) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector4`](./Vector4.html) | 目标向量 |
| `dst?` | [`Vector4`](./Vector4.html) | - |

#### [#](#Returns-20) Returns

[`Vector4`](./Vector4.html)

计算结果

---

### [#](#toArray) toArray

▸ **toArray**(): `number`[]

返回向量数据

**`memberof`** Vector4

#### [#](#Returns-21) Returns

`number`[]

矩阵数据，以JSArray返回

---

### [#](#createFromArray) createFromArray

▸ `Static` **createFromArray**(`array`): [`Vector4`](./Vector4.html)

使用一个数组创建
此操作会拷贝一份数组

**`static`**

**`memberof`** Vector4

#### [#](#Parameters-15) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `array` | `number`[] | 数据源，长度必须为4，否则会抛出异常 |

#### [#](#Returns-22) Returns

[`Vector4`](./Vector4.html)

创建出来的向量

---

### [#](#createFromNumber) createFromNumber

▸ `Static` **createFromNumber**(`x`, `y`, `z`, `w`): [`Vector4`](./Vector4.html)

使用数值创建
推荐使用这种方式代替new Vector4

**`static`**

**`memberof`** Vector4

#### [#](#Parameters-16) Parameters

| Name | Type |
| --- | --- |
| `x` | `number` |
| `y` | `number` |
| `z` | `number` |
| `w` | `number` |

#### [#](#Returns-23) Returns

[`Vector4`](./Vector4.html)

创建出来的向量

---

### [#](#createFromTypedArray) createFromTypedArray

▸ `Static` **createFromTypedArray**(`array`, `offset?`): [`Vector4`](./Vector4.html)

使用某个已有的typedArray创建
此操作不会拷贝数据，而是在原来的内存区域上操作

**`static`**

**`memberof`** Vector4

#### [#](#Parameters-17) Parameters

| Name | Type | Default value | Description |
| --- | --- | --- | --- |
| `array` | `Float32Array` | `undefined` | 数据源 |
| `offset` | `number` | `0` | - |

#### [#](#Returns-24) Returns

[`Vector4`](./Vector4.html)

Incorrect translation.