# [#](#粒子发射器) 粒子发射器

## [#](#构建粒子发射器) 构建粒子发射器

粒子系统目前内置了不同形态的发射器类型，通过对相关参数的调整，满足开发者所需要的粒子效果。

目前支持以下发射器类型:

- PointShape 点状发射器
- SphereShape 球形发射器
- BoxShape 箱形发射器
- ConeShape 锥形发射器
- CircleShape 圆形发射器

通过`emitter-type`指定发射器类型。`emitter-props`可以配置发射器参数，示例如下：

```
<xr-particle capacity="20" emit-rate="10" life-time="1.5 2" speed="0.4 0.8" size="0.3 0.5"
emitter-type="SphereShape" emitter-props="radius:1,randomizeDirection:0"></xr-particle>
```

不同发射器可以指定的相关参数如下:

### [#](#BoxShapeEmitter-箱形发射器) `BoxShapeEmitter` 箱形发射器

| 参数名称 | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| direction | Vector3 | 粒子初始发射方向左区间 | (0, 1.0, 0) |
| direction2 | Vector3 | 粒子初始发射方向右区间 | (0, 1.0, 0) |
| minEmitBox | Vector3 | 粒子初始位置左区间 | (-0.5, -0.5, -0.5) |
| maxEmitBox | Vector3 | 粒子初始位置右区间 | (0.5, 0.5, 0.5) |

### [#](#CircleShapeEmitter-圆形发射器) `CircleShapeEmitter` 圆形发射器

| 参数名称 | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| radius | number | 粒子随机生成圆形区域的半径 | 1 |
| radiusRange | number | 粒子在圆形区域内的覆盖范围 [0-1] | 0 |
| direction | Vector3 | 粒子初始发射方向左区间 | (0, 1.0, 0) |
| direction2 | Vector3 | 粒子初始发射方向右区间 | (0, 1.0, 0) |
| arc | number | 规定粒子生成的扇形区域角度大小 [0-360] | 360 |

### [#](#ConeShapeEmitter-锥形发射器) `ConeShapeEmitter` 锥形发射器

| 参数名称 | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| radius | number | 粒子随机生成锥型区域的半径 | 3 |
| radiusRange | number | 粒子在锥型区域内的覆盖范围 [0-1] | 0 |
| heightRange | number | 粒子在高度方向上的覆盖范围 [0-1] | 1 |
| arc | number | 规定粒子生成的扇形区域角度大小 [0-360] | 360 |
| randomizeDirection | number | 粒子发射方向的扰动程度 [0-1] | 0 |

### [#](#PointShapeEmitter-点状发射器) `PointShapeEmitter` 点状发射器

| 参数名称 | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| direction | Vector3 | 粒子初始发射方向左区间 | (0, 1.0, 0) |
| direction2 | Vector3 | 粒子初始发射方向右区间 | (0, 1.0, 0) |

### [#](#SphereShapeEmitter-球形发射器) `SphereShapeEmitter` 球形发射器

| 参数名称 | 类型 | 备注 | 默认值 |
| --- | --- | --- | --- |
| radius | number | 粒子随机生成球型区域的半径 | 3 |
| radiusRange | number | 粒子在球型区域内的覆盖范围 [0-1] | 0 |
| arc | number | 规定粒子生成的扇形区域角度大小 [0-360] | 360 |
| randomizeDirection | number | 粒子发射方向的扰动程度 [0-1] | 0 |

### [#](#控制粒子系统运作) 控制粒子系统运作

通过调用stop函数, 可以对当前粒子效果进行暂停。

```
 particleComponent.stop()
```

通过调用start函数, 播放粒子效果。

```
 particleComponent.start() // 可以设置参数，如: particleComponent.start(2), 延时二秒启动
```

### [#](#通过代码构建发射器) 通过代码构建发射器

系统支持通过代码动态创建发射器，这种生成方式可以对发射器的具体参数进行设置, 这里以点型态发射器为例。

首先需要获得元素的实例，详情见[element元素](./element.html), 并获取对应的组件,详情见[component组件](./component.html)

```
 particleComponent.createPointEmitter(direction1, direction2)
```

## [#](#通过自定义粒子发射过程构建一副画作) 通过自定义粒子发射过程构建一副画作

粒子运作的轨迹由粒子发射器规定的粒子运动矢量`direction`大小与粒子初始位置`position`决定，这一运作过程均由粒子系统进行模拟运算。

为了实现特殊的粒子效果，每个发射器中支持定义粒子运作接口`processInstance`, 这里以粒子复现一副图片效果为例。

```
    // 记录图片数据的二元数组content, 取值范围[0~1]
    var content = ..

    //设置箱型发射器的发射方向，与粒子初始位置范围
    particleComponent.createBoxEmitter(direction1, direction2, minEmitBox, maxEmitBox);

    //实现发射器的自定义粒子运作接口, 声明参数instance代表每个粒子实例，deltaTime为根据渲染更新的时间，均由系统自动传入
    particleComponent.particleEmitter.processInstance = (instance, deltaTime) => {
      var contentTemp = content
      var cellNumY = contentTemp.length
      var cellNumX = contentTemp[0].length
      // 影响画作的大小与粒子疏密程度的因子
      var step = 0.02
      // 实际渲染出的画作高度
      var height = Math.floor(step * content.length)
      // 实际渲染出的画作宽度
      var width =  Math.floor(step * cellNumX)
      if(instance.position.x - instance.particleSystem.emitterPosition.x> width){
        instance.age = instance.lifeTime;
            return;
        }
        instance.age = 0;
        const posX = Math.floor((instance.position.x -  instance.particleSystem.emitterPosition.x)/ step);
        const posY = Math.floor(instance.position.y/ step);
        const speed = contentTemp[cellNumY-1-posY][posX] * 0.97;
        instance.position.x += ( 1 - speed * 0.97 ) * 0.03 + Math.random() * 0.007;
        instance.color.w = speed * 0.3;
    };
```

这里介绍有关每个**粒子实例**的相关属性，用户可以在`processInstance`接口中设计它们的运作规律

### [#](#粒子实例相关属性) 粒子实例相关属性

| 名称 | 类型 | 备注 |
| --- | --- | --- |
| angle | number | 粒子的偏移角度 |
| color | Vector4 | 粒子颜色 |
| direction | Vector3 | 粒子的运动方向 |
| particleSystem | Particle | 粒子所归属的粒子系统 |
| position | Vector3 | 粒子所处位置 |
| size | number | 粒子大小 |

Incorrect translation.