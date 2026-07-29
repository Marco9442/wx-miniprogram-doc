# [#](#刚体和全局物理) 刚体和全局物理

> ⚠️ 刚体物理功能目前尚在Beta阶段，并且需要2.32.1及之后的基础库才能使用。

## [#](#全局物理) 全局物理

要让当前的场景成为一个物理世界，需要先在`<xr-scene>`下配置一个`<xr-physics>`标签：

```
<xr-scene>
    <xr-physics />
    ...(场景中的其他标签)
</xr-scene>
```

> ⚠️ `<xr-physics>`标签只能位于`<xr-scene>`下一级，不能放置在更深的层级中。

### [#](#全局物理配置) 全局物理配置

可以通过修改在`<xr-physics>`上的属性来配置全局物理参数（目前仅开放了少数配置项）：

| 属性名 | 描述 | 值类型 | 备注 |
| --- | --- | --- | --- |
| disabled | 是否禁用物理 | boolean | `disable=true`的话，效果和不存在`<xr-physics>`标签时一致。 |
| gravity | 全局重力 | Vector3 | 默认重力(0, -9.8, 0) |

## [#](#刚体) 刚体

在标签上添加`rigidbody`属性来使其成为一个刚体：

```
<xr-mesh ... rigidbody />
```

添加之后就能观察到物体受重力影响而下落了。

### [#](#刚体配置) 刚体配置

通过为`rigidbody`属性添加属性值来修改刚体配置：

```
<xr-mesh ... rigidbody="mass: 5.0" />
```

| 属性值 | 描述 | 值类型 | 备注 |
| --- | --- | --- | --- |
| disabled | 是否禁用刚体 | boolean | `disable=true`的话，效果和不存在rigidbody属性时一致。 |
| mass | 刚体质量 | number | mass > 0 |
| useGravity | 是否受重力影响 | boolean |  |
| constraintsMask | 限制刚体在某个轴上的移动 | number | 具体指参考 @TODO |

### [#](#刚体组件) 刚体组件

标签上的`rigidbody`属性对应元素上的`Rigidbody`组件。  
使用`Rigidbody`组件上的方法可以移动刚体或者修改刚体属性：

| 方法名 | 描述 | 备注 |
| --- | --- | --- |
| addForce / addTorque | 是否禁用刚体 | 对刚体施加力，产生加速度。 |
| sleep / wakeUp | 强制刚体睡眠/唤醒 | 正常情况下睡眠状态是由物理引擎自动管理的，如果发现刚体异常静止，可以尝试手动wakeUp。 |

Incorrect translation.