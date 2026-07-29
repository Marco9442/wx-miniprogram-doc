# [#](#Aggregate-addFields-object-Object-Aggregate) <Aggregate>.addFields(object: Object): <Aggregate>

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

聚合阶段。添加新字段到输出的记录。经过 `addFields` 聚合阶段，输出的所有记录中除了输入时带有的字段外，还将带有 `addFields` 指定的字段。

## [#](#参数) 参数

### [#](#object-Object) object: Object

## [#](#返回值) 返回值

### [#](#Aggregate) <Aggregate>

## [#](#API-说明) API 说明

`addFields` 等同于同时指定了所有已有字段和新增字段的 `project` 阶段。

`addFields` 的形式如下：

```
addFields({
  <新字段>: <表达式>
})
```

`addFields` 可指定多个新字段，每个新字段的值由使用的表达式决定。

如果指定的新字段与原有字段重名，则新字段的值会覆盖原有字段的值。注意 `addFields` 不能用来给数组字段添加元素。

## [#](#示例-1：连续两次-addFields) 示例 1：连续两次 addFields

假设集合 `scores` 有如下记录：

```
{
  _id: 1,
  student: "Maya",
  homework: [ 10, 5, 10 ],
  quiz: [ 10, 8 ],
  extraCredit: 0
}
{
  _id: 2,
  student: "Ryan",
  homework: [ 5, 6, 5 ],
  quiz: [ 8, 8 ],
  extraCredit: 8
}
```

应用两次 `addFields`，第一次增加两个字段分别为 `homework` 和 `quiz` 的和值，第二次增加一个字段再基于上两个和值求一次和值。

```
const $ = db.command.aggregate
db.collection('scores').aggregate()
  .addFields({
    totalHomework: $.sum('$homework'),
    totalQuiz: $.sum('$quiz')
  })
  .addFields({
    totalScore: $.add(['$totalHomework', '$totalQuiz', '$extraCredit'])
  })
  .end()
```

返回结果如下：

```
{
  "_id" : 1,
  "student" : "Maya",
  "homework" : [ 10, 5, 10 ],
  "quiz" : [ 10, 8 ],
  "extraCredit" : 0,
  "totalHomework" : 25,
  "totalQuiz" : 18,
  "totalScore" : 43
}
{
  "_id" : 2,
  "student" : "Ryan",
  "homework" : [ 5, 6, 5 ],
  "quiz" : [ 8, 8 ],
  "extraCredit" : 8,
  "totalHomework" : 16,
  "totalQuiz" : 16,
  "totalScore" : 40
}
```

## [#](#示例-2：在嵌套记录里增加字段) 示例 2：在嵌套记录里增加字段

可以用点表示法在嵌套记录里增加字段。假设 `vehicles` 集合含有如下记录：

```
{ _id: 1, type: "car", specs: { doors: 4, wheels: 4 } }
{ _id: 2, type: "motorcycle", specs: { doors: 0, wheels: 2 } }
{ _id: 3, type: "jet ski" }
```

可以用如下操作在 `specs` 字段下增加一个新的字段 `fuel_type`，值都设为固定字符串 `unleaded`：

```
db.collection('vehicles').aggregate()
  .addFields({
    'specs.fuel_type': 'unleaded'
  })
  .end()
```

返回结果如下：

```
{ _id: 1, type: "car",
   specs: { doors: 4, wheels: 4, fuel_type: "unleaded" } }
{ _id: 2, type: "motorcycle",
   specs: { doors: 0, wheels: 2, fuel_type: "unleaded" } }
{ _id: 3, type: "jet ski",
   specs: { fuel_type: "unleaded" } }
```

## [#](#示例-3：设置字段值为另一个字段) 示例 3：设置字段值为另一个字段

可以通过 `$` 加字段名组成的字符串作为值的表达式来设置字段的值为另一个字段的值。

同样用上一个集合示例，可以用如下操作添加一个字段 `vehicle_type`，将其值设置为 `type` 字段的值：

```
db.collection('vehicles').aggregate()
  .addFields({
    vehicle_type: '$type'
  })
  .end()
```

返回结果如下：

```
{ _id: 1, type: "car", vehicle_type: "car",
   specs: { doors: 4, wheels: 4, fuel_type: "unleaded" } }
{ _id: 2, type: "motorcycle", vehicle_type: "motorcycle",
   specs: { doors: 0, wheels: 2, fuel_type: "unleaded" } }
{ _id: 3, type: "jet ski", vehicle_type: "jet ski",
   specs: { fuel_type: "unleaded" } }
```

Incorrect translation.