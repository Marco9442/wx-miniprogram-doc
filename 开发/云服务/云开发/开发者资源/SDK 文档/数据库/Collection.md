# [#](#Collection) Collection

数据库集合引用

## [#](#方法) 方法

### [#](#Collection-doc-id-string-Document) <Collection.doc>(id: string): <Document>

获取集合中指定记录的引用。方法接受一个 id 参数，指定需引用的记录的 \_id。

### [#](#Collection-add-options-Object-Promise-Object) [Collection.add](collection/Collection.add)(options: Object): Promise<Object>

新增记录，如果传入的记录对象没有 \_id 字段，则由后台自动生成 \_id；若指定了 \_id，则不能与已有记录冲突

### [#](#Collection-aggregate-Aggregate) [Collection.aggregate](collection/Collection.aggregate)(): [Aggregate](aggregate/Aggregate)

发起[聚合](../../guide/database/aggregation/aggregation)操作，定义完聚合流水线阶段之后需调用 `end` 方法标志结束定义并实际发起聚合操作

### [#](#Collection-count-Promise-Object) [Collection.count](collection/Collection.count)(): Promise<Object>

统计匹配查询条件的记录的条数

### [#](#Collection-field-projection-Object-Collection) [Collection.field](collection/Collection.field)(projection: Object): <Collection>

指定返回结果中记录需返回的字段

### [#](#Collection-get-Promise-Object) [Collection.get](collection/Collection.get)(): Promise<Object>

获取集合数据，或获取根据查询条件筛选后的集合数据。

### [#](#Collection-limit-value-number-Collection) [Collection.limit](collection/Collection.limit)(value: number): <Collection>

指定查询结果集数量上限

### [#](#Collection-orderBy-fieldPath-string-string-order-Collection) [Collection.orderBy](collection/Collection.orderBy)(fieldPath: string, string: order): <Collection>

指定查询排序条件

### [#](#Collection-remove-Promise-Object) [Collection.remove](collection/Collection.remove)(): Promise<Object>

删除多条记录。注意只支持通过匹配 `where` 语句来删除，不支持 `skip` 和 `limit`。

### [#](#Collection-skip-offset-number-Collection) [Collection.skip](collection/Collection.skip)(offset: number): <Collection>

指定查询返回结果时从指定序列后的结果开始返回，常用于分页

### [#](#Collection-update-Promise-Object) [Collection.update](collection/Collection.update)(): Promise<Object>

更新多条记录

### [#](#Collection-watch-options-Object-Object) [Collection.watch](collection/Collection.watch)(options: Object): Object

监听集合中符合查询条件的数据的更新事件。使用 `watch` 时，支持 `where`, `orderBy`, `limit`，不支持 `field`。

### [#](#Collection-where-condition-Object-Collection) [Collection.where](collection/Collection.where)(condition: Object): <Collection>

指定查询条件，返回带新查询条件的新的集合引用

Incorrect translation.