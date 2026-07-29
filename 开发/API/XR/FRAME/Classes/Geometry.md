[xr-frame](./../) / [Exports](./../modules.html) / Geometry

# [#](#Class-Geometry) Class: Geometry

几何资源，用于定义渲染中的图元数据。

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Geometry.html#constructor)

### [#](#Accessors) Accessors

- [boundBall](./Geometry.html#boundBall)
- [boundBox](./Geometry.html#boundBox)
- [indexBuffer](./Geometry.html#indexBuffer)
- [indexData](./Geometry.html#indexData)
- [vertexBuffer](./Geometry.html#vertexBuffer)
- [vertexData](./Geometry.html#vertexData)
- [vertexLayout](./Geometry.html#vertexLayout)

### [#](#Methods) Methods

- [addSubMesh](./Geometry.html#addSubMesh)
- [getIndiceLength](./Geometry.html#getIndiceLength)
- [getIndiceStart](./Geometry.html#getIndiceStart)
- [getMaterialIndex](./Geometry.html#getMaterialIndex)
- [getSubMeshCount](./Geometry.html#getSubMeshCount)
- [getVertexLayout](./Geometry.html#getVertexLayout)
- [modifySubMesh](./Geometry.html#modifySubMesh)
- [setBoundBall](./Geometry.html#setBoundBall)
- [setBoundBox](./Geometry.html#setBoundBox)
- [uploadIndexBuffer](./Geometry.html#uploadIndexBuffer)
- [uploadVertexBuffer](./Geometry.html#uploadVertexBuffer)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Geometry**(`_scene`, `vertexLayout`, `vBuffer`, `iBuffer`, `indexType?`)

构造一个`Geometry`。

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `_scene` | [`Scene`](./Scene.html) |
| `vertexLayout` | `default` |
| `vBuffer` | `ArrayBufferView` |
| `iBuffer` | `ArrayBufferView` |
| `indexType` | [`EIndexType`](./../enums/EIndexType.html) |

## [#](#Accessors-2) Accessors

### [#](#boundBall) boundBall

• `get` **boundBall**(): [`BoundBall`](./BoundBall.html)

包围球，只读。

#### [#](#Returns) Returns

[`BoundBall`](./BoundBall.html)

---

### [#](#boundBox) boundBox

• `get` **boundBox**(): [`BoundBox`](./BoundBox.html)

包围盒，只读。

#### [#](#Returns-2) Returns

[`BoundBox`](./BoundBox.html)

---

### [#](#indexBuffer) indexBuffer

• `get` **indexBuffer**(): `default`

获取IndexBuffer。

#### [#](#Returns-3) Returns

`default`

---

### [#](#indexData) indexData

• `get` **indexData**(): `default`

获取IndexData。
这种类型的索引数据用于合批，只对于开启了`dynamicBatch`的Renderer有效。
注意如果已经获取过`indexBuffer`，将无效。

#### [#](#Returns-4) Returns

`default`

---

### [#](#vertexBuffer) vertexBuffer

• `get` **vertexBuffer**(): `default`

获取VertexBuffer。

#### [#](#Returns-5) Returns

`default`

---

### [#](#vertexData) vertexData

• `get` **vertexData**(): `default`

获取VertexData。
这种类型的顶点数据用于合批，只对于开启了`dynamicBatch`的Renderer有效。
注意如果已经获取过`vertexBuffer`，将无效。

#### [#](#Returns-6) Returns

`default`

---

### [#](#vertexLayout) vertexLayout

• `get` **vertexLayout**(): `default`

获取VertexLayout。

#### [#](#Returns-7) Returns

`default`

## [#](#Methods-2) Methods

### [#](#addSubMesh) addSubMesh

▸ **addSubMesh**(`length`, `offset`, `materialIndex?`): `void`

增加subMesh。

#### [#](#Parameters-2) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `length` | `number` | 索引长度 |
| `offset` | `number` | 索引起始偏移 |
| `materialIndex?` | `number` | - |

#### [#](#Returns-8) Returns

`void`

---

### [#](#getIndiceLength) getIndiceLength

▸ **getIndiceLength**(`subMeshIndex`): `number`

获取指定序号的subMesh的索引长度

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `subMeshIndex` | `number` |

#### [#](#Returns-9) Returns

`number`

索引长度，返回-1代表SubMesh不存在

---

### [#](#getIndiceStart) getIndiceStart

▸ **getIndiceStart**(`subMeshIndex`): `number`

获取指定序号的subMesh的索引起始点

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `subMeshIndex` | `number` |

#### [#](#Returns-10) Returns

`number`

索引起始点,返回-1代表SubMesh不存在

---

### [#](#getMaterialIndex) getMaterialIndex

▸ **getMaterialIndex**(`subMeshIndex`): `number`

获取指定序号的subMesh的材质序号

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `subMeshIndex` | `number` |

#### [#](#Returns-11) Returns

`number`

材质序号，返回-1代表subMesh不存在

---

### [#](#getSubMeshCount) getSubMeshCount

▸ **getSubMeshCount**(): `number`

获取当前mesh有多少subMesh

#### [#](#Returns-12) Returns

`number`

---

### [#](#getVertexLayout) getVertexLayout

▸ **getVertexLayout**(): `default`

获取VertexLayout。

#### [#](#Returns-13) Returns

`default`

---

### [#](#modifySubMesh) modifySubMesh

▸ **modifySubMesh**(`subMeshIndex`, `length`, `offset`): `boolean`

修改subMesh。

#### [#](#Parameters-6) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `subMeshIndex` | `number` | - |
| `length` | `number` | 索引长度 |
| `offset` | `number` | 索引起始偏移 |

#### [#](#Returns-14) Returns

`boolean`

---

### [#](#setBoundBall) setBoundBall

▸ **setBoundBall**(`center`, `radius`): `void`

动态更新包围球。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `center` | [`Vector3`](./Vector3.html) |
| `radius` | `number` |

#### [#](#Returns-15) Returns

`void`

---

### [#](#setBoundBox) setBoundBox

▸ **setBoundBox**(`center`, `size`, `autoUpdateBall?`): `void`

动态更新包围盒，默认会自动计算包围球。

#### [#](#Parameters-8) Parameters

| Name | Type | Default value |
| --- | --- | --- |
| `center` | [`Vector3`](./Vector3.html) | `undefined` |
| `size` | [`Vector3`](./Vector3.html) | `undefined` |
| `autoUpdateBall` | `boolean` | `true` |

#### [#](#Returns-16) Returns

`void`

---

### [#](#uploadIndexBuffer) uploadIndexBuffer

▸ **uploadIndexBuffer**(`offset`, `buffer`): `void`

更新IndexBuffer。
仅在获取了`indexBuffer`后有效。

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `offset` | `number` |
| `buffer` | `Uint16Array` | `Uint32Array` |

#### [#](#Returns-17) Returns

`void`

---

### [#](#uploadVertexBuffer) uploadVertexBuffer

▸ **uploadVertexBuffer**(`offset`, `buffer`): `void`

更新VertexBuffer。
仅在获取了`vertexBuffer`后有效。

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `offset` | `number` |
| `buffer` | `ArrayBufferView` |

#### [#](#Returns-18) Returns

`void`

Incorrect translation.