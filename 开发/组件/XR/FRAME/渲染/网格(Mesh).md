# [#](#网格) 网格

网格[Mesh](/miniprogram/dev/api/xr-frame/classes/Mesh)是一种组件，严格来讲应该称为**网格渲染器**，但出于精简就这么命名了。其作用是组织起[几何数据](./geometry.html)和[材质](./material.html)实现渲染的载体。

## [#](#创建一个网格) 创建一个网格

网格一般在`xml`中创建，可以直接以组件模式使用或者是用代理的封装元素`xr-mesh`，此封装元素派生自[节点](./../core/node.html)。

组件的方式：

```
<xr-node mesh="geometry:cube;material:mat" />
```

元素的模式：

```
<xr-mesh geometry="cube" uniforms="u_baseColorMap:waifu" states="cullOn:false" cast-shadow receive-shadow />
```

以上案例我们可以看到网格的所有数据，其中`geometry`是必传的，值为注册过的几何数据的资源id。`material`是创建过的材质的资源id，如果不写则会默认使用一个标准的使用了`standard`效果的材质。

`uniforms`和`states`比较特殊，它们其实是材质的数据，但为了方便开发者使用，不去给每一个网格都创建一个材质，所以我们提供了这样的一种方式。在这种方式下，**会自动拷贝一份材质，对材质的修改不会影响到原始材质，同时对原始材质的修改也不会影响到这个网格**，这点一定要注意！

最后的`castShadow`和`receiveShadow`是阴影相关的数据，详细可见[灯光](./light.html)中相关的部分。

Incorrect translation.