# [#](#Transaction) Transaction

数据库事务操作对象

## [#](#方法) 方法

### [#](#Transaction-collection-name-string-Collection) <Transaction.collection>(name: string): [Collection](../Collection)

事务中获取集合的引用。方法接受一个 name 参数，指定需引用的集合名称。

### [#](#Transaction-commit-reason-any-Promise-void) <Transaction.commit>(reason: any): Promise<void>

提交事务

### [#](#Transaction-rollback-reason-any-Promise-void) <Transaction.rollback>(reason: any): Promise<void>

终止并回滚事务

## [#](#API-列表) API 列表

```
transaction
|-- collection       获取集合引用
|   |-- doc          获取记录引用
|   |   |-- get      获取记录内容
|   |   |-- update   更新记录内容
|   |   |-- set      替换记录内容
|   |   |-- remove   删除记录
|   |-- add          新增记录
|-- rollback         终止事务并回滚
|-- commit           提交事务（仅在使用 startTransaction 时可调用）
```

Incorrect translation.