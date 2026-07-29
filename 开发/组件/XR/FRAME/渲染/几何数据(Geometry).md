# [#](#几何数据) 几何数据

渲染的基础之一是几何数据[Geometry](/miniprogram/dev/api/xr-frame/classes/Geometry)资源，它描述了一个模型的顶点信息、索引信息以及顶点的存取结构。

一般来讲，几何数据是通过模型中自动加载，或使用 [内置Geometry](./../builtin/geometry.html)，但有时候我们需要去定制一些程序化生成的数据比如粒子等等，所以还是要明白如何去定制。

## [#](#定制一个看看) 定制一个看看

```
const geometry = scene.createGeometry(
  vertexLayout, vertexBuffer,
  indexBuffer, indexType
)
```

可见构造一个`Geometry`需要提供好几个参数，他们是：

### [#](#VertexLayout) VertexLayout

首先是`VertexLayout`，用于描述顶点布局，举个例子来说：

```
const layout = new xrFrameSystem.VertexLayout({
  attributes: [
    {
      name: 'a_position',
      format: xrFrameSystem.EVertexFormat.FLOAT2,
      offset: 0,
      usage: xrFrameSystem.EVertexLayoutUsage.POSITION,
    },
    {
      name: 'a_texCoord',
      offset: 8,
      format: xrFrameSystem.EVertexFormat.FLOAT2,
      usage: xrFrameSystem.EVertexLayoutUsage.UV0,
    },
    {
      name: 'a_color',
      format: xrFrameSystem.EVertexFormat.UBYTE4,
      offset: 16,
      usage: xrFrameSystem.EVertexLayoutUsage.COLOR,
    }
  ],
  stride: 20
});
```

这里定义了一个自定义的`VertexLayout`，其中有两个参数：

1. attributes：描述了顶点的结构，即如何GPU将如何理解传入的顶点数据，比如第一个元素，其表示此顶点属性在shader中名字为`a_position`，格式是`FLOAT2`，在顶点Buffer中偏移为0，并且用做`POSITION`。
2. stride：描述了每个顶点所占带宽的字节数。
3. `usage`会影响到渲染这些数据时开启的宏，详见[内置效果](./../builtin/effect.html)。

### [#](#Buffer和Type) Buffer和Type

后面三个参数分别是**顶点数据**、**索引数据**和**索引格式**，顶点数据**按照布局结构**存储着整个Geometry的顶点数据，索引数据存储着**图元对顶点的索引**，而索引格式则是决定了索引数据的存储格式，其可以为`UINT16`或者`UINT32`，如果为`UINT16`，则索引数据中的顶点索引值**不得超过65535**。

## [#](#设置参数) 设置参数

在创建完一个新的几何数据后，开发者还需要设置一些参数来让它正确得运作起来，主要是SubMesh和包围球/包围盒。

### [#](#SubMesh) SubMesh

有了数据和布局后，几何数据还需要提供一些信息去让渲染器知道如何使用这些数据，我们提供了叫做`SubMesh`的抽象，来将Geometry分割为数个部分：

```
// 添加一个SubMesh，其索引数据长度为`length`个顶点，第一个索引偏移为`offset`
geometry.addSubMesh(length, offset);

// 修改第`subMeshIndex`位置的SubMesh信息
geometry.modifySubMesh(subMeshIndex, length, offset);
```

这样分割的原因主要是即便是同一个几何数据，也可能拥有不同的**材质**来处理不同的部分，但是出于综合考虑，**目前渲染时几何数据和材质是一一对应的，所以只支持一个`SubMesh`**。

### [#](#包围球和包围盒) 包围球和包围盒

对于每个几何数据来说，在相机的剔除阶段，都需要一个包围球/包围盒来决定其是否在可视范围内，开发者可以通过以下方案来设置包围球：

```
// `center`为球心相对于模型原点的偏移，`radius`是球的半径
geometry.setBoundBall(center, radius);
```

或是设置包围盒：

```
// `center`为球心相对于模型原点的偏移，`size`是盒的三维长度，默认会同步更新包围球
geometry.setBoundBox(center, size);
```

### [#](#更新数据) 更新数据

在某些场合，开发者还会需要去动态更新顶点或索引数据，比如粒子系统，我们也提供了一些方案来完成这种需求（注意这种更新操作只能在Mesh已经被提交到GPU后使用）：

```
// 从字节偏移`offset`开始，将`buffer`整个更新到顶点数据。
geometry.uploadVertexBuffer(offset, buffer);

// 从字节偏移`offset`开始，将`buffer`整个更新到索引数据。
geometry.uploadIndexBuffer(offset, buffer);
```

之后便可以使用这个几何数据了。

## [#](#注册到资源系统) 注册到资源系统

和其他资源一样，我们提供了一套注册机制来让开发者定制在`xml`中也可以被引用的几何数据：

```
xrFrameSystem.registerGeometry('custom', scene => {
  return scene.createGeometry(
    vertexLayout, vertexBuffer,
    indexBuffer, indexType
  );
});
```

注册后在`schema`中类型指定为`geometry`的数据，便可以使用`custom`这个资源id引用到创建的资源了。

Incorrect translation.