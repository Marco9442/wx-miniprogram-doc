[xr-frame](./../) / [Exports](./../modules.html) / Matrix4

# [#](#Class-Matrix4) Class: Matrix4

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Matrix4.html#constructor)

### [#](#Accessors) Accessors

- [IDENTITY](./Matrix4.html#IDENTITY)

### [#](#Methods) Methods

- [axisRotate](./Matrix4.html#axisRotate)
- [clone](./Matrix4.html#clone)
- [decomposeTransRotMatScale](./Matrix4.html#decomposeTransRotMatScale)
- [getColumn](./Matrix4.html#getColumn)
- [getRow](./Matrix4.html#getRow)
- [getValue](./Matrix4.html#getValue)
- [inverse](./Matrix4.html#inverse)
- [multiply](./Matrix4.html#multiply)
- [print](./Matrix4.html#print)
- [rotateByQuaternion](./Matrix4.html#rotateByQuaternion)
- [scale](./Matrix4.html#scale)
- [set](./Matrix4.html#set)
- [setArray](./Matrix4.html#setArray)
- [setColumn](./Matrix4.html#setColumn)
- [setRow](./Matrix4.html#setRow)
- [setValue](./Matrix4.html#setValue)
- [toArray](./Matrix4.html#toArray)
- [transformDirection](./Matrix4.html#transformDirection)
- [transformPoint](./Matrix4.html#transformPoint)
- [transformVector](./Matrix4.html#transformVector)
- [translate](./Matrix4.html#translate)
- [transpose](./Matrix4.html#transpose)
- [xRotate](./Matrix4.html#xRotate)
- [yRotate](./Matrix4.html#yRotate)
- [zRotate](./Matrix4.html#zRotate)
- [composeFromRST3](./Matrix4.html#composeFromRST3)
- [composeTQS](./Matrix4.html#composeTQS)
- [composeTRS](./Matrix4.html#composeTRS)
- [createFromArray](./Matrix4.html#createFromArray)
- [createFromTypedArray](./Matrix4.html#createFromTypedArray)
- [createRotationAxis](./Matrix4.html#createRotationAxis)
- [createRotationX](./Matrix4.html#createRotationX)
- [createRotationY](./Matrix4.html#createRotationY)
- [createRotationZ](./Matrix4.html#createRotationZ)
- [fromQuaternion](./Matrix4.html#fromQuaternion)
- [lookAt](./Matrix4.html#lookAt)
- [orthographic](./Matrix4.html#orthographic)
- [perspective](./Matrix4.html#perspective)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Matrix4**(`raw?`, `offset?`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `raw?` | `Float32Array` |
| `offset?` | `number` |

## [#](#Accessors-2) Accessors

### [#](#IDENTITY) IDENTITY

• `Static` `get` **IDENTITY**(): [`Matrix4`](./Matrix4.html)

单位矩阵

**`readonly`**

**`static`**

**`memberof`** Matrix4

#### [#](#Returns) Returns

[`Matrix4`](./Matrix4.html)

单位矩阵，每次返回都会创建新的对象

## [#](#Methods-2) Methods

### [#](#axisRotate) axisRotate

▸ **axisRotate**(`axis`, `angleInRadians`, `dst?`): [`Matrix4`](./Matrix4.html)

将该矩阵绕指定轴旋转

**`memberof`** Matrix4

#### [#](#Parameters-2) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `axis` | [`Vector3`](./Vector3.html) | 轴向量 |
| `angleInRadians` | `number` | 旋转幅度，用弧度表示 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-2) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#clone) clone

▸ **clone**(): [`Matrix4`](./Matrix4.html)

拷贝该矩阵

**`memberof`** Matrix4

#### [#](#Returns-3) Returns

[`Matrix4`](./Matrix4.html)

拷贝出来的对象

---

### [#](#decomposeTransRotMatScale) decomposeTransRotMatScale

▸ **decomposeTransRotMatScale**(`dstTranslation`, `dstRotationMatrix`, `dstScale`): `boolean`

分解RTS矩阵为位移、旋转、缩放向量，返回是否成功

**`memberof`** Matrix4

#### [#](#Parameters-3) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `dstTranslation` | [`Vector3`](./Vector3.html) | 目标位移向量 |
| `dstRotationMatrix` | [`Matrix4`](./Matrix4.html) | 目标旋转矩阵 |
| `dstScale` | [`Vector3`](./Vector3.html) | 目标缩放分量 |

#### [#](#Returns-4) Returns

`boolean`

分解是否成功，如不成功，可能是缩放分量为0

---

### [#](#getColumn) getColumn

▸ **getColumn**(`column`, `dst?`): [`Vector4`](./Vector4.html)

获取矩阵某列

**`memberof`** Matrix4

#### [#](#Parameters-4) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `column` | `number` | 列数 |
| `dst?` | [`Vector4`](./Vector4.html) | - |

#### [#](#Returns-5) Returns

[`Vector4`](./Vector4.html)

该列数据

---

### [#](#getRow) getRow

▸ **getRow**(`row`, `dst?`): [`Vector4`](./Vector4.html)

获取矩阵某行

**`memberof`** Matrix4

#### [#](#Parameters-5) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `row` | `number` | 行数 |
| `dst?` | [`Vector4`](./Vector4.html) | - |

#### [#](#Returns-6) Returns

[`Vector4`](./Vector4.html)

该行数据

---

### [#](#getValue) getValue

▸ **getValue**(`column`, `row`): `number`

获取矩阵某行某列的值

**`memberof`** Matrix4

#### [#](#Parameters-6) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `column` | `number` | 列数 |
| `row` | `number` | 行数 |

#### [#](#Returns-7) Returns

`number`

自身

---

### [#](#inverse) inverse

▸ **inverse**(`dst?`): [`Matrix4`](./Matrix4.html)

求该矩阵的逆

**`memberof`** Matrix4

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `dst?` | [`Matrix4`](./Matrix4.html) |

#### [#](#Returns-8) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#multiply) multiply

▸ **multiply**(`m`, `dst?`): [`Matrix4`](./Matrix4.html)

将该矩阵与另一个矩阵相乘

**`memberof`** Matrix4

#### [#](#Parameters-8) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `m` | [`Matrix4`](./Matrix4.html) | 右乘矩阵 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-9) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#print) print

▸ **print**(): `void`

#### [#](#Returns-10) Returns

`void`

---

### [#](#rotateByQuaternion) rotateByQuaternion

▸ **rotateByQuaternion**(`quaternion`, `dst?`): [`Matrix4`](./Matrix4.html)

将该矩阵使用指定四元数旋转

**`memberof`** Matrix4

#### [#](#Parameters-9) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `quaternion` | [`Quaternion`](./Quaternion.html) | 四元数 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-11) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#scale) scale

▸ **scale**(`sx`, `sy`, `sz`, `dst?`): [`Matrix4`](./Matrix4.html)

将该矩阵进行缩放变换

**`memberof`** Matrix4

#### [#](#Parameters-10) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `sx` | `number` | x轴缩放 |
| `sy` | `number` | y轴缩放 |
| `sz` | `number` | z轴缩放 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-12) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#set) set

▸ **set**(`val`): [`Matrix4`](./Matrix4.html)

拷贝目标矩阵的值到该矩阵

**`memberof`** Matrix4

#### [#](#Parameters-11) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `val` | [`Matrix4`](./Matrix4.html) | 目标 |

#### [#](#Returns-13) Returns

[`Matrix4`](./Matrix4.html)

自身

---

### [#](#setArray) setArray

▸ **setArray**(`value`, `offset?`): [`Matrix4`](./Matrix4.html)

#### [#](#Parameters-12) Parameters

| Name | Type |
| --- | --- |
| `value` | `ArrayLike`<`number`> |
| `offset?` | `number` |

#### [#](#Returns-14) Returns

[`Matrix4`](./Matrix4.html)

---

### [#](#setColumn) setColumn

▸ **setColumn**(`vec`, `column`): [`Matrix4`](./Matrix4.html)

设置矩阵某列

**`memberof`** Matrix4

#### [#](#Parameters-13) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `vec` | [`Vector4`](./Vector4.html) | 列向量 |
| `column` | `number` | 列数 |

#### [#](#Returns-15) Returns

[`Matrix4`](./Matrix4.html)

自身

---

### [#](#setRow) setRow

▸ **setRow**(`vec`, `row`): [`Matrix4`](./Matrix4.html)

设置矩阵某行

**`memberof`** Matrix4

#### [#](#Parameters-14) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `vec` | [`Vector4`](./Vector4.html) | 行向量 |
| `row` | `number` | 行数 |

#### [#](#Returns-16) Returns

[`Matrix4`](./Matrix4.html)

自身

---

### [#](#setValue) setValue

▸ **setValue**(`value`, `column`, `row`): [`Matrix4`](./Matrix4.html)

设置该矩阵某行某列的值

**`memberof`** Matrix4

#### [#](#Parameters-15) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `value` | `number` | 值 |
| `column` | `number` | 列数 |
| `row` | `number` | 行数 |

#### [#](#Returns-17) Returns

[`Matrix4`](./Matrix4.html)

自身

---

### [#](#toArray) toArray

▸ **toArray**(): `number`[]

返回矩阵数据

**`memberof`** Matrix4

#### [#](#Returns-18) Returns

`number`[]

矩阵数据，以JSArray返回

---

### [#](#transformDirection) transformDirection

▸ **transformDirection**(`dir`, `dst?`): [`Vector3`](./Vector3.html)

矩阵变换作用于方向

**`memberof`** Matrix4

#### [#](#Parameters-16) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `dir` | [`Vector3`](./Vector3.html) | 方向 |
| `dst?` | [`Vector3`](./Vector3.html) | - |

#### [#](#Returns-19) Returns

[`Vector3`](./Vector3.html)

计算结果

---

### [#](#transformPoint) transformPoint

▸ **transformPoint**(`p`, `dst?`): [`Vector3`](./Vector3.html)

矩阵变换作用于点

**`memberof`** Matrix4

#### [#](#Parameters-17) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `p` | [`Vector3`](./Vector3.html) | 点 |
| `dst?` | [`Vector3`](./Vector3.html) | - |

#### [#](#Returns-20) Returns

[`Vector3`](./Vector3.html)

计算结果

---

### [#](#transformVector) transformVector

▸ **transformVector**(`v`, `dst?`): [`Vector4`](./Vector4.html)

矩阵变换作用于向量

**`memberof`** Matrix4

#### [#](#Parameters-18) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `v` | [`Vector4`](./Vector4.html) | 向量 |
| `dst?` | [`Vector4`](./Vector4.html) | - |

#### [#](#Returns-21) Returns

[`Vector4`](./Vector4.html)

计算结果

---

### [#](#translate) translate

▸ **translate**(`tx`, `ty`, `tz`, `dst?`): [`Matrix4`](./Matrix4.html)

将该矩阵进行位移变换

**`memberof`** Matrix4

#### [#](#Parameters-19) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `tx` | `number` | x轴位移 |
| `ty` | `number` | y轴位移 |
| `tz` | `number` | z轴位移 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-22) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#transpose) transpose

▸ **transpose**(`dst?`): [`Matrix4`](./Matrix4.html)

求该矩阵的转置

**`memberof`** Matrix4

#### [#](#Parameters-20) Parameters

| Name | Type |
| --- | --- |
| `dst?` | [`Matrix4`](./Matrix4.html) |

#### [#](#Returns-23) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#xRotate) xRotate

▸ **xRotate**(`rx`, `dst?`): [`Matrix4`](./Matrix4.html)

将该矩阵绕x轴旋转

**`memberof`** Matrix4

#### [#](#Parameters-21) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `rx` | `number` | 旋转幅度，用弧度表示 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-24) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#yRotate) yRotate

▸ **yRotate**(`ry`, `dst?`): [`Matrix4`](./Matrix4.html)

将该矩阵绕y轴旋转

**`memberof`** Matrix4

#### [#](#Parameters-22) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `ry` | `number` | 旋转幅度，用弧度表示 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-25) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#zRotate) zRotate

▸ **zRotate**(`rz`, `dst?`): [`Matrix4`](./Matrix4.html)

将该矩阵绕z轴旋转

**`memberof`** Matrix4

#### [#](#Parameters-23) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `rz` | `number` | 旋转幅度，用弧度表示 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-26) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#composeFromRST3) composeFromRST3

▸ `Static` **composeFromRST3**(`m3`, `dst?`): [`Matrix4`](./Matrix4.html)

从二维RST矩阵扩展到三维RST矩阵

**`static`**

**`memberof`** Matrix4

#### [#](#Parameters-24) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `m3` | [`Matrix3`](./Matrix3.html) | 二维RST矩阵 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-27) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#composeTQS) composeTQS

▸ `Static` **composeTQS**(`translation`, `rotation`, `scale`, `dst?`): [`Matrix4`](./Matrix4.html)

将位移旋转缩放合成一个RST矩阵，旋转用四元数表示

**`static`**

**`memberof`** Matrix4

#### [#](#Parameters-25) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `translation` | [`Vector3`](./Vector3.html) | 位移向量 |
| `rotation` | [`Quaternion`](./Quaternion.html) | 旋转四元数 |
| `scale` | [`Vector3`](./Vector3.html) | 缩放向量 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-28) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#composeTRS) composeTRS

▸ `Static` **composeTRS**(`translation`, `rotation`, `scale`, `dst?`): [`Matrix4`](./Matrix4.html)

将位移旋转缩放合成一个RST矩阵，旋转用矩阵表示

**`static`**

**`memberof`** Matrix4

#### [#](#Parameters-26) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `translation` | [`Vector3`](./Vector3.html) | 位移向量 |
| `rotation` | [`Matrix4`](./Matrix4.html) | 旋转矩阵 |
| `scale` | [`Vector3`](./Vector3.html) | 缩放向量 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-29) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#createFromArray) createFromArray

▸ `Static` **createFromArray**(`array`): [`Matrix4`](./Matrix4.html)

使用一个数组创建
此操作会拷贝一份数组

**`static`**

**`memberof`** Matrix4

#### [#](#Parameters-27) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `array` | `number`[] | 数据源，长度必须为16，否则会抛出异常 |

#### [#](#Returns-30) Returns

[`Matrix4`](./Matrix4.html)

创建出来的矩阵

---

### [#](#createFromTypedArray) createFromTypedArray

▸ `Static` **createFromTypedArray**(`array`, `offset?`): [`Matrix4`](./Matrix4.html)

使用某个已有的typedArray创建
此操作不会拷贝数据，而是在原来的内存区域上操作

**`static`**

**`memberof`** Matrix4

#### [#](#Parameters-28) Parameters

| Name | Type | Default value | Description |
| --- | --- | --- | --- |
| `array` | `Float32Array` | `undefined` | 数据源 |
| `offset` | `number` | `0` | - |

#### [#](#Returns-31) Returns

[`Matrix4`](./Matrix4.html)

创建出来的矩阵

---

### [#](#createRotationAxis) createRotationAxis

▸ `Static` **createRotationAxis**(`axis`, `angleInRadians`, `dst?`): [`Matrix4`](./Matrix4.html)

创建绕指定轴旋转的矩阵

**`static`**

**`memberof`** Matrix4

#### [#](#Parameters-29) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `axis` | [`Vector3`](./Vector3.html) | 旋转轴 |
| `angleInRadians` | `number` | 旋转幅度，用弧度表示 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-32) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#createRotationX) createRotationX

▸ `Static` **createRotationX**(`rad`, `dst?`): [`Matrix4`](./Matrix4.html)

创建绕X轴旋转的矩阵

**`static`**

**`memberof`** Matrix4

#### [#](#Parameters-30) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `rad` | `number` | 旋转幅度，用弧度表示 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-33) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#createRotationY) createRotationY

▸ `Static` **createRotationY**(`rad`, `dst?`): [`Matrix4`](./Matrix4.html)

创建绕Y轴旋转的矩阵

**`static`**

**`memberof`** Matrix4

#### [#](#Parameters-31) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `rad` | `number` | 旋转幅度，用弧度表示 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-34) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#createRotationZ) createRotationZ

▸ `Static` **createRotationZ**(`rad`, `dst?`): [`Matrix4`](./Matrix4.html)

创建绕Z轴旋转的矩阵

**`static`**

**`memberof`** Matrix4

#### [#](#Parameters-32) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `rad` | `number` | 旋转轴 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-35) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#fromQuaternion) fromQuaternion

▸ `Static` **fromQuaternion**(`quat`, `dst?`): [`Matrix4`](./Matrix4.html)

将四元数转换为旋转矩阵

**`static`**

**`memberof`** Matrix4

#### [#](#Parameters-33) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `quat` | [`Quaternion`](./Quaternion.html) | 四元数 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-36) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#lookAt) lookAt

▸ `Static` **lookAt**(`position`, `target`, `up`, `dst?`): [`Matrix4`](./Matrix4.html)

构造相机矩阵

**`static`**

**`memberof`** Matrix4

#### [#](#Parameters-34) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `position` | [`Vector3`](./Vector3.html) | 相机位置 |
| `target` | [`Vector3`](./Vector3.html) | 相机目标位置 |
| `up` | [`Vector3`](./Vector3.html) | 上方向 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-37) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#orthographic) orthographic

▸ `Static` **orthographic**(`left`, `right`, `bottom`, `top`, `near`, `far`, `dst?`): [`Matrix4`](./Matrix4.html)

构造正交投影矩阵

**`static`**

**`memberof`** Matrix4

#### [#](#Parameters-35) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `left` | `number` | 左平面 |
| `right` | `number` | 右平面 |
| `bottom` | `number` | 上平面 |
| `top` | `number` | 下平面 |
| `near` | `number` | 近平面 |
| `far` | `number` | 远平面 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-38) Returns

[`Matrix4`](./Matrix4.html)

计算结果

---

### [#](#perspective) perspective

▸ `Static` **perspective**(`fieldOfViewRadians`, `aspect`, `near`, `far`, `dst?`): [`Matrix4`](./Matrix4.html)

构造透视投影矩阵

**`static`**

**`memberof`** Matrix4

#### [#](#Parameters-36) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `fieldOfViewRadians` | `number` | 视野大小，用弧度表示 |
| `aspect` | `number` | 宽高比 |
| `near` | `number` | 近平面 |
| `far` | `number` | 远平面 |
| `dst?` | [`Matrix4`](./Matrix4.html) | - |

#### [#](#Returns-39) Returns

[`Matrix4`](./Matrix4.html)

计算结果

Incorrect translation.