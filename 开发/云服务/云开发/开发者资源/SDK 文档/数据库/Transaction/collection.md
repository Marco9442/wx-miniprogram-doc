# [#](#Transaction-collection-name-string-Collection) <Transaction>.collection(name: string): [Collection](../Collection)

> 支持端：[云函数](../../../reference/changelog-server-sdk)

事务中获取集合的引用。方法接受一个 name 参数，指定需引用的集合名称。

## [#](#参数) 参数

### [#](#name-string) name: string

集合名称

## [#](#返回值) 返回值

### [#](#Collection) [Collection](../Collection)

集合引用

## [#](#注意事项) 注意事项

在事务中仅能进行单记录操作，也就是不能使用 `where`、`aggregate` 接口，可以使用的接口如下：

```
collection       获取集合引用
|-- add          新增记录
|-- doc          获取记录引用
    |-- get      获取记录内容
    |-- update   更新记录内容
    |-- set      替换记录内容
    |-- remove   删除记录
```

Incorrect translation.