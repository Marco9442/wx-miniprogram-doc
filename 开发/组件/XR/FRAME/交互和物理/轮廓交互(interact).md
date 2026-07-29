# [#](#轮廓间交互) 轮廓间交互

> ⚠️ 轮廓间交互功能目前尚在Beta阶段，并且需要2.32.1及之后的基础库才能使用。

## [#](#碰撞与重叠) 碰撞与重叠

碰撞和重叠是不同的概念：

- 碰撞是指：两个轮廓发生物理学碰撞，并因此而改变位置与速度，产生碰撞事件；
- 重叠是指：两个轮廓在位置上发生了重叠，并产生重叠事件，**不**发生物理学碰撞。

## [#](#需要轮廓才能发生交互) 需要轮廓才能发生交互

`碰撞`和`重叠`是在两个轮廓之前发生的行为，所以在添加交互属性之前，请先确保为物体创建了[轮廓](./shape.html)。

## [#](#轮廓交互组件) 轮廓交互组件

通过为标签添加`shape-interact`属性来设置轮廓间交互：

```
<xr-mesh ... mesh-shape shape-interact>
```

设置`shape-interact`属性后会自动为对应元素创建`ShapeInteract`组件。

### [#](#组件属性) 组件属性

| 属性值 | 描述 | 值类型 | 备注 |
| --- | --- | --- | --- |
| disabled | 是否禁用交互 | boolean | `disable=true`的话，效果和不存在shape-interact属性时一致 |
| collide | 是否发生碰撞 | boolean | `collide=true`的话，发生碰撞，否则发生重叠，**默认`false`** |
| bounciness | 弹性系数 | number | 0≤bounciness≤1，仅当`collide=true`时生效 |
| staticFriction | 静摩擦系数 | number | 0≤staticFriction≤1，仅当`collide=true`时生效 |
| dynamicFriction | 动摩擦系数 | number | 0≤staticFriction≤1，仅当`collide=true`时生效 |

> ⚠️ 只有两个物体的collide都为true，他们之间才能发生碰撞！

## [#](#交互事件) 交互事件

在两个轮廓之间发生交互时，会产生交互事件，可以在标签上绑定相关绑定事件回调：

```
<xr-mesh ... mesh-shape shape-interact bind:overlap-begin="handleOverlapBegin">
```

事件一共有以下6种：

| 事件名 | 描述 | 事件回调参数 |
| --- | --- | --- |
| collide-begin | 发生碰撞 | ICollideEvent |
| collide-persist | 碰撞持续 | ICollideEvent |
| collide-exit | 碰撞结束 | ICollideEvent |
| overlap-begin | 发生重叠 | IOverlapEvent |
| overlap-persist | 重叠持续 | IOverlapEvent |
| overlap-exit | 重叠结束 | IOverlapEvent |

其中xxx-begin和xxx-exit会成对地出现，从相交的第二帧开始xxx-persist每帧都会生成一次。

Incorrect translation.