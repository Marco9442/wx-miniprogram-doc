[xr-frame](./../) / [Exports](./../modules.html) / Vector2

# [#](#Class-Vector2) Class: Vector2

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Vector2.html#constructor)

### [#](#Properties) Properties

- [ONE](./Vector2.html#ONE)
- [ZERO](./Vector2.html#ZERO)

### [#](#Accessors) Accessors

- [x](./Vector2.html#x)
- [y](./Vector2.html#y)

### [#](#Methods) Methods

- [add](./Vector2.html#add)
- [clone](./Vector2.html#clone)
- [dot](./Vector2.html#dot)
- [equal](./Vector2.html#equal)
- [getAngle](./Vector2.html#getAngle)
- [isZero](./Vector2.html#isZero)
- [length](./Vector2.html#length)
- [lerp](./Vector2.html#lerp)
- [negate](./Vector2.html#negate)
- [normalize](./Vector2.html#normalize)
- [scale](./Vector2.html#scale)
- [set](./Vector2.html#set)
- [setArray](./Vector2.html#setArray)
- [setValue](./Vector2.html#setValue)
- [sub](./Vector2.html#sub)
- [toArray](./Vector2.html#toArray)
- [createFromArray](./Vector2.html#createFromArray)
- [createFromNumber](./Vector2.html#createFromNumber)
- [createFromTypedArray](./Vector2.html#createFromTypedArray)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Vector2**(`raw?`, `offset?`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `raw?` | `Float32Array` |
| `offset?` | `number` |

## [#](#Properties-2) Properties

### [#](#ONE) ONE

▪ `Static` `Readonly` **ONE**: [`Vector2`](./Vector2.html)

一向量，不要对该对象进行修改

**`readonly`**

**`static`**

**`memberof`** Vector3

---

### [#](#ZERO) ZERO

▪ `Static` `Readonly` **ZERO**: [`Vector2`](./Vector2.html)

零向量，不要对该对象进行修改

**`readonly`**

**`static`**

**`memberof`** Vector3

## [#](#Accessors-2) Accessors

### [#](#x) x

• `get` **x**(): `number`

x值

**`memberof`** Vector2

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

**`memberof`** Vector2

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

## [#](#Methods-2) Methods

### [#](#add) add

▸ **add**(`v`, `dst?`): [`Vector2`](./Vector2.html)

向量加法

**`memberof`** Vector2

#### [#](#Parameters-4) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector2`](./Vector2.html) | 目标向量 |
| `dst?` | [`Vector2`](./Vector2.html) | - |

#### [#](#Returns-5) Returns

[`Vector2`](./Vector2.html)

计算结果

---

### [#](#clone) clone

▸ **clone**(): [`Vector2`](./Vector2.html)

拷贝该向量

**`memberof`** Vector2

#### [#](#Returns-6) Returns

[`Vector2`](./Vector2.html)

拷贝出来的对象

---

### [#](#dot) dot

▸ **dot**(`v`): `number`

向量点乘

**`memberof`** Vector2

#### [#](#Parameters-5) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector2`](./Vector2.html) | 目标向量 |

#### [#](#Returns-7) Returns

`number`

计算结果

---

### [#](#equal) equal

▸ **equal**(`v`): `boolean`

判断与目标向量的值是否相等

**`memberof`** Vector2

#### [#](#Parameters-6) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector2`](./Vector2.html) | 目标向量 |

#### [#](#Returns-8) Returns

`boolean`

是否相等，这里误差小于10^-6视为相等

---

### [#](#getAngle) getAngle

▸ **getAngle**(): `number`

获取向量旋转角，以角度表示

**`memberof`** Vector2

#### [#](#Returns-9) Returns

`number`

旋转角，以角度表示

---

### [#](#isZero) isZero

▸ **isZero**(): `boolean`

是否为零向量

**`memberof`** Vector2

#### [#](#Returns-10) Returns

`boolean`

---

### [#](#length) length

▸ **length**(): `number`

向量的模

**`memberof`** Vector2

#### [#](#Returns-11) Returns

`number`

计算结果

---

### [#](#lerp) lerp

▸ **lerp**(`v`, `f`, `dst?`): [`Vector2`](./Vector2.html)

在该向量与目标向量之间计算插值

**`memberof`** Vector2

#### [#](#Parameters-7) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector2`](./Vector2.html) | 目标向量 |
| `f` | `number` | 插值系数 |
| `dst?` | [`Vector2`](./Vector2.html) | - |

#### [#](#Returns-12) Returns

[`Vector2`](./Vector2.html)

计算结果

---

### [#](#negate) negate

▸ **negate**(): [`Vector2`](./Vector2.html)

取反

#### [#](#Returns-13) Returns

[`Vector2`](./Vector2.html)

---

### [#](#normalize) normalize

▸ **normalize**(`dst?`): [`Vector2`](./Vector2.html)

向量归一化，如该向量为零向量，则结果依然为零向量

**`memberof`** Vector2

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `dst?` | [`Vector2`](./Vector2.html) |

#### [#](#Returns-14) Returns

[`Vector2`](./Vector2.html)

计算结果

---

### [#](#scale) scale

▸ **scale**(`f`, `dst?`): [`Vector2`](./Vector2.html)

向量缩放

**`memberof`** Vector2

#### [#](#Parameters-9) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `f` | `number` | 缩放比 |
| `dst?` | [`Vector2`](./Vector2.html) | - |

#### [#](#Returns-15) Returns

[`Vector2`](./Vector2.html)

计算结果

---

### [#](#set) set

▸ **set**(`val`): [`Vector2`](./Vector2.html)

拷贝目标向量的值到该向量

**`memberof`** Vector2

#### [#](#Parameters-10) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `val` | [`Vector2`](./Vector2.html) | 目标向量 |

#### [#](#Returns-16) Returns

[`Vector2`](./Vector2.html)

自身

---

### [#](#setArray) setArray

▸ **setArray**(`value`, `offset?`): [`Vector2`](./Vector2.html)

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `value` | `ArrayLike`<`number`> |
| `offset?` | `number` |

#### [#](#Returns-17) Returns

[`Vector2`](./Vector2.html)

---

### [#](#setValue) setValue

▸ **setValue**(`x`, `y`): [`Vector2`](./Vector2.html)

设置向量的值

**`memberof`** Vector2

#### [#](#Parameters-12) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `x` | `number` | x值 |
| `y` | `number` | y值 |

#### [#](#Returns-18) Returns

[`Vector2`](./Vector2.html)

自身

---

### [#](#sub) sub

▸ **sub**(`v`, `dst?`): [`Vector2`](./Vector2.html)

向量减法

**`memberof`** Vector2

#### [#](#Parameters-13) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector2`](./Vector2.html) | 目标向量 |
| `dst?` | [`Vector2`](./Vector2.html) | - |

#### [#](#Returns-19) Returns

[`Vector2`](./Vector2.html)

计算结果

---

### [#](#toArray) toArray

▸ **toArray**(): `number`[]

返回向量数据

**`memberof`** Vector2

#### [#](#Returns-20) Returns

`number`[]

矩阵数据，以JSArray返回

---

### [#](#createFromArray) createFromArray

▸ `Static` **createFromArray**(`array`): [`Vector2`](./Vector2.html)

使用一个数组创建
此操作会拷贝一份数组

**`static`**

**`memberof`** Vector2

#### [#](#Parameters-14) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `array` | `number`[] | 数据源，长度必须为2，否则会抛出异常 |

#### [#](#Returns-21) Returns

[`Vector2`](./Vector2.html)

创建出来的向量

---

### [#](#createFromNumber) createFromNumber

▸ `Static` **createFromNumber**(`x`, `y`): [`Vector2`](./Vector2.html)

使用数值创建
推荐使用这种方式代替new Vector2

**`static`**

**`memberof`** Vector2

#### [#](#Parameters-15) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `x` | `number` | x |
| `y` | `number` | y |

#### [#](#Returns-22) Returns

[`Vector2`](./Vector2.html)

创建出来的向量

---

### [#](#createFromTypedArray) createFromTypedArray

▸ `Static` **createFromTypedArray**(`array`, `offset?`): [`Vector2`](./Vector2.html)

使用某个已有的typedArray创建
此操作不会拷贝数据，而是在原来的内存区域上操作

**`static`**

**`memberof`** Vector2

#### [#](#Parameters-16) Parameters

| Name | Type | Default value | Description |
| --- | --- | --- | --- |
| `array` | `Float32Array` | `undefined` | 数据源 |
| `offset` | `number` | `0` | - |

#### [#](#Returns-23) Returns

[`Vector2`](./Vector2.html)

创建出来的向量

Incorrect translation.