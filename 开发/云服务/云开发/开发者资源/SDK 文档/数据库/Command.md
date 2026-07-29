# [#](#Command) Command

数据库操作符，通过 `db.command` 获取

## [#](#属性) 属性

### [#](#AggregateCommand-aggregate) [AggregateCommand](command/aggregate/AggregateCommand) aggregate

聚合操作符

## [#](#方法) 方法

### [#](#Command-addToSet-value-any-Object-Command) [Command.addToSet](command/Command.addToSet)(value: any|Object): <Command>

数组更新操作符。原子操作。给定一个或多个元素，除非数组中已存在该元素，否则添加进数组。

### [#](#Command-all-values-any-Command) [Command.all](command/Command.all)(values: any[]): <Command>

数组查询操作符。用于数组字段的查询筛选条件，要求数组字段中包含给定数组的所有元素。

### [#](#Command-and-expressions-any-Command) [Command.and](command/Command.and)(expressions: any[]): <Command>

查询操作符，用于表示逻辑 "与" 的关系，表示需同时满足多个查询筛选条件

### [#](#Command-bit-object-Object-Command) [Command.bit](command/Command.bit)(object: Object): <Command>

更新操作符。对字段进行位运算，可以进行 and/or/xor 运算。

### [#](#Command-elemMatch-condition-Object-Command-Command) [Command.elemMatch](command/Command.elemMatch)(condition: Object|<Command>): <Command>

用于数组字段的查询筛选条件，要求数组中包含至少一个满足 `elemMatch` 给定的所有条件的元素

### [#](#Command-eq-value-any-Command) [Command.eq](command/Command.eq)(value: any): <Command>

查询筛选条件，表示字段等于某个值。`eq` 指令接受一个字面量 (literal)，可以是 `number`, `boolean`, `string`, `object`, `array`, `Date`。

### [#](#Command-exists-value-boolean-Command) [Command.exists](command/Command.exists)(value: boolean): <Command>

判断字段是否存在

### [#](#Command-expr-aggregateExpression-Expression-Command) [Command.expr](command/Command.expr)(aggregateExpression: [Expression](aggregate/Expression)): <Command>

查询操作符，用于在查询语句中使用聚合表达式，方法接收一个参数，该参数必须为聚合表达式

### [#](#Command-geoIntersects-options-Object-Command) [Command.geoIntersects](command/Command.geoIntersects)(options: Object): <Command>

找出给定的地理位置图形相交的记录

### [#](#Command-geoNear-options-Object-Command) [Command.geoNear](command/Command.geoNear)(options: Object): <Command>

按从近到远的顺序，找出字段值在给定点的附近的记录。

### [#](#Command-geoWithin-options-Object-Command) [Command.geoWithin](command/Command.geoWithin)(options: Object): <Command>

找出字段值在指定区域内的记录，无排序。指定的区域必须是多边形（Polygon）或多边形集合（MultiPolygon）。

### [#](#Command-gt-value-any-Command) [Command.gt](command/Command.gt)(value: any): <Command>

查询筛选操作符，表示需大于指定值。可以传入 `Date` 对象用于进行日期比较。

### [#](#Command-gte-value-any-Command) [Command.gte](command/Command.gte)(value: any): <Command>

查询筛选操作符，表示需大于或等于指定值。可以传入 `Date` 对象用于进行日期比较。

### [#](#Command-in-value-any-Command) [Command.in](command/Command.in)(value: any[]): <Command>

查询筛选操作符，表示要求值在给定的数组内。

### [#](#Command-inc-value-number-Command) [Command.inc](command/Command.inc)(value: number): <Command>

更新操作符，原子操作，用于指示字段自增

### [#](#Command-lt-value-any-Command) [Command.lt](command/Command.lt)(value: any): <Command>

查询筛选操作符，表示需小于指定值。可以传入 `Date` 对象用于进行日期比较。

### [#](#Command-lte-value-any-Command) [Command.lte](command/Command.lte)(value: any): <Command>

查询筛选操作符，表示需小于或等于指定值。可以传入 `Date` 对象用于进行日期比较。

### [#](#Command-max-value-any-Command) [Command.max](command/Command.max)(value: any): <Command>

更新操作符，给定一个值，只有该值大于字段当前值才进行更新。

### [#](#Command-min-value-any-Command) [Command.min](command/Command.min)(value: any): <Command>

更新操作符，给定一个值，只有该值小于字段当前值才进行更新。

### [#](#Command-mod-divisor-number-remainder-number-Command) [Command.mod](command/Command.mod)(divisor: number, remainder: number): <Command>

查询筛选操作符，给定除数 divisor 和余数 remainder，要求字段作为被除数时 value % divisor = remainder。

### [#](#Command-mul-value-number-Command) [Command.mul](command/Command.mul)(value: number): <Command>

更新操作符，原子操作，用于指示字段自乘某个值

### [#](#Command-neq-value-any-Command) [Command.neq](command/Command.neq)(value: any): <Command>

查询筛选条件，表示字段不等于某个值。`eq` 指令接受一个字面量 (literal)，可以是 `number`, `boolean`, `string`, `object`, `array`, `Date`。

### [#](#Command-nin-value-any-Command) [Command.nin](command/Command.nin)(value: any[]): <Command>

查询筛选操作符，表示要求值不在给定的数组内。

### [#](#Command-nor-expressions-any-Command) [Command.nor](command/Command.nor)(expressions: any[]): <Command>

查询操作符，用于表示逻辑 "都不" 的关系，表示需不满足指定的所有条件。如果记录中没有对应的字段，则默认满足条件。

### [#](#Command-not-command-Command-Command) [Command.not](command/Command.not)(command: <Command>): <Command>

查询操作符，用于表示逻辑 "非" 的关系，表示需不满足指定的条件。

### [#](#Command-or-expressions-any-Command) [Command.or](command/Command.or)(expressions: any[]): <Command>

查询操作符，用于表示逻辑 "或" 的关系，表示需同时满足多个查询筛选条件。或指令有两种用法，一是可以进行字段值的 “或” 操作，二是也可以进行跨字段的 “或” 操作。

### [#](#Command-pop-Command) [Command.pop](command/Command.pop)(): <Command>

数组更新操作符，对一个值为数组的字段，将数组尾部元素删除

### [#](#Command-pull-value-any-Command) [Command.pull](command/Command.pull)(value: any): <Command>

数组更新操作符。给定一个值或一个查询条件，将数组中所有匹配给定值或查询条件的元素都移除掉。

### [#](#Command-pullAll-value-any-Command) [Command.pullAll](command/Command.pullAll)(value: any): <Command>

数组更新操作符。给定一个值或一个查询条件，将数组中所有匹配给定值的元素都移除掉。跟 `pull` 的差别在于只能指定常量值、传入的是数组。

### [#](#Command-push-values-Object-Command) [Command.push](command/Command.push)(values: Object): <Command>

数组更新操作符。对一个值为数组的字段，往数组添加一个或多个值。或字段原为空，则创建该字段并设数组为传入值。

### [#](#Command-remove-Command) [Command.remove](command/Command.remove)(): <Command>

更新操作符，用于表示删除某个字段。

### [#](#Command-rename-value-string-Command) [Command.rename](command/Command.rename)(value: string): <Command>

更新操作符，字段重命名。如果需要对嵌套深层的字段做重命名，需要用点路径表示法。不能对嵌套在数组里的对象的字段进行重命名。

### [#](#Command-set-value-any-Command) [Command.set](command/Command.set)(value: any): <Command>

更新操作符，用于设定字段等于指定值。

### [#](#Command-shift-Command) [Command.shift](command/Command.shift)(): <Command>

数组更新操作符，对一个值为数组的字段，将数组头部元素删除。

### [#](#Command-size-value-string-Command) [Command.size](command/Command.size)(value: string): <Command>

更新操作符，用于数组字段的查询筛选条件，要求数组长度为给定值

### [#](#Command-unshift-values-any-Command) [Command.unshift](command/Command.unshift)(values: any[]): <Command>

数组更新操作符，对一个值为数组的字段，往数组头部添加一个或多个值。或字段原为空，则创建该字段并设数组为传入值。

Incorrect translation.