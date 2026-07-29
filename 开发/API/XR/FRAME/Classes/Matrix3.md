[xr-frame](./../) / [Exports](./../modules.html) / Matrix3

# [#](#Class-Matrix3) Class: Matrix3

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Matrix3.html#constructor)

### [#](#Accessors) Accessors

- [raw](./Matrix3.html#raw)
- [IDENTITY](./Matrix3.html#IDENTITY)

### [#](#Methods) Methods

- [inverse](./Matrix3.html#inverse)
- [multiply](./Matrix3.html#multiply)
- [rotate](./Matrix3.html#rotate)
- [scale](./Matrix3.html#scale)
- [setArray](./Matrix3.html#setArray)
- [toArray](./Matrix3.html#toArray)
- [transformPoint](./Matrix3.html#transformPoint)
- [translate](./Matrix3.html#translate)
- [createFromArray](./Matrix3.html#createFromArray)
- [createFromTypedArray](./Matrix3.html#createFromTypedArray)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Matrix3**(`raw?`, `offset?`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `raw?` | `Float32Array` |
| `offset?` | `number` |

## [#](#Accessors-2) Accessors

### [#](#raw) raw

• `get` **raw**(): `Float32Array`

#### [#](#Returns) Returns

`Float32Array`

---

### [#](#IDENTITY) IDENTITY

• `Static` `get` **IDENTITY**(): [`Matrix3`](./Matrix3.html)

单位矩阵

**`readonly`**

**`static`**

**`memberof`** Matrix3

#### [#](#Returns-2) Returns

[`Matrix3`](./Matrix3.html)

单位矩阵，每次返回都会创建新的对象

## [#](#Methods-2) Methods

### [#](#inverse) inverse

▸ **inverse**(`dst?`): [`Matrix3`](./Matrix3.html)

求该矩阵的逆

**`memberof`** Matrix3

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `dst?` | [`Matrix3`](./Matrix3.html) |

#### [#](#Returns-3) Returns

[`Matrix3`](./Matrix3.html)

计算结果

---

### [#](#multiply) multiply

▸ **multiply**(`m`, `dst?`): [`Matrix3`](./Matrix3.html)

将该矩阵与另一个矩阵相乘

**`memberof`** Matrix3

#### [#](#Parameters-3) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `m` | [`Matrix3`](./Matrix3.html) | 右乘矩阵 |
| `dst?` | [`Matrix3`](./Matrix3.html) | - |

#### [#](#Returns-4) Returns

[`Matrix3`](./Matrix3.html)

计算结果

---

### [#](#rotate) rotate

▸ **rotate**(`radians`, `dst?`): [`Matrix3`](./Matrix3.html)

将该矩阵进行旋转变换

**`memberof`** Matrix3

#### [#](#Parameters-4) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `radians` | `number` | 旋转幅度，用弧度表示 |
| `dst?` | [`Matrix3`](./Matrix3.html) | - |

#### [#](#Returns-5) Returns

[`Matrix3`](./Matrix3.html)

计算结果

---

### [#](#scale) scale

▸ **scale**(`sx`, `sy`, `dst?`): [`Matrix3`](./Matrix3.html)

将该矩阵进行缩放变换

**`memberof`** Matrix3

#### [#](#Parameters-5) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `sx` | `number` | x轴缩放 |
| `sy` | `number` | y轴缩放 |
| `dst?` | [`Matrix3`](./Matrix3.html) | - |

#### [#](#Returns-6) Returns

[`Matrix3`](./Matrix3.html)

计算结果

---

### [#](#setArray) setArray

▸ **setArray**(`value`, `offset?`): [`Matrix3`](./Matrix3.html)

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `value` | `ArrayLike`<`number`> |
| `offset?` | `number` |

#### [#](#Returns-7) Returns

[`Matrix3`](./Matrix3.html)

---

### [#](#toArray) toArray

▸ **toArray**(): `number`[]

返回矩阵数据

**`memberof`** Matrix3

#### [#](#Returns-8) Returns

`number`[]

矩阵数据，以JSArray返回

---

### [#](#transformPoint) transformPoint

▸ **transformPoint**(`v`, `dst?`): [`Vector2`](./Vector2.html)

矩阵变换作用于点

**`memberof`** Matrix3

#### [#](#Parameters-7) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector2`](./Vector2.html) | 点 |
| `dst?` | [`Vector2`](./Vector2.html) | - |

#### [#](#Returns-9) Returns

[`Vector2`](./Vector2.html)

计算结果

---

### [#](#translate) translate

▸ **translate**(`tx`, `ty`, `dst?`): [`Matrix3`](./Matrix3.html)

将该矩阵进行位移变换

**`memberof`** Matrix3

#### [#](#Parameters-8) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `tx` | `number` | x轴位移 |
| `ty` | `number` | y轴位移 |
| `dst?` | [`Matrix3`](./Matrix3.html) | - |

#### [#](#Returns-10) Returns

[`Matrix3`](./Matrix3.html)

计算结果

---

### [#](#createFromArray) createFromArray

▸ `Static` **createFromArray**(`array`): [`Matrix3`](./Matrix3.html)

使用一个数组创建
此操作会拷贝一份数组

**`static`**

**`memberof`** Matrix3

#### [#](#Parameters-9) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `array` | `number`[] | 数据源，长度必须为9，否则会抛出异常 |

#### [#](#Returns-11) Returns

[`Matrix3`](./Matrix3.html)

创建出来的矩阵

---

### [#](#createFromTypedArray) createFromTypedArray

▸ `Static` **createFromTypedArray**(`array`, `offset?`): [`Matrix3`](./Matrix3.html)

使用某个已有的typedArray创建
此操作不会拷贝数据，而是在原来的内存区域上操作

**`static`**

**`memberof`** Matrix3

#### [#](#Parameters-10) Parameters

| Name | Type | Default value | Description |
| --- | --- | --- | --- |
| `array` | `Float32Array` | `undefined` | 数据源 |
| `offset` | `number` | `0` | - |

#### [#](#Returns-12) Returns

[`Matrix3`](./Matrix3.html)

创建出来的矩阵

Incorrect translation.