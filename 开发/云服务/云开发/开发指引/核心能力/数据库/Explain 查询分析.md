## [#](#Explain-查询分析) Explain 查询分析

> 基础库 2.12.0、开发者工具 1.03.2006242 起

数据库 Explain API 是帮助开发者分析查询语句的 API，它的使用方法也很简单，在需要进行查询语句分析的数据库 API 入参中传入 `explain: true`，则 API 的返回值会变成该查询的分析结果，包括查询语句的执行计划、执行情况（包括索引使用情况）、及系统层面对查询语句的修改。为防止误操作，该 API 仅会在开发者工具中生效。简要示例：

执行 JS 语句，注意多了个 `explain: true` 的参数：

```
db.collection('test').where({
  _openid: '{openid}',
}).get({
  explain: true,
  complete: console.log,
})
```

此时的返回结果示例：

![](https://res8.wxqcloud.qq.com.cn/wxdoc/76798cf4-be3b-4758-b4a5-7601fc885158.png)

### [#](#支持-explain-的接口) 支持 explain 的接口

所有涉及到查询的接口都支持 explain，包括：

- db.collection.where.get
- db.collection.where.count
- db.collection.where.update
- db.collection.where.remove
- db.collection.aggregate.end

### [#](#explain-返回值说明) explain 返回值说明

返回值包含三个字段，queryPlanner, executionStats, 和 queryModifications

#### [#](#queryPlanner) queryPlanner

包含执行计划信息。下面列出部分字段说明。如果是分片的集合，会用 shards 数组区分开每个分片的执行计划，其数据结构是一致的。

**queryPlanner.winningPlan**

最终数据库选择的执行计划。一个执行计划会表示为处理阶段树，即一个阶段可以有一个输入阶段（inputStage）或多个输入阶段（inputStages）。

**queryPlanner.winningPlan.stage**

处理阶段的名称。每个阶段都会有阶段相关的信息字段。

**queryPlanner.winningPlan.inputStage**

仅在父阶段只有一个子阶段时存在。包含子阶段/输入阶段信息。

**queryPlanner.winningPlan.inputStages**

仅在父阶段只有超过一个子阶段时存在。包含子阶段/输入阶段信息。

**queryPlanner.rejectedPlans**

被放弃的执行计划。

#### [#](#executionStats) executionStats

包含执行情况信息。对写操作，只会说明会执行的修改操作，并不会实际写入。如果是分片的集合，会用 shards 数组区分开每个分片的执行情况，其数据结构是一致的。

**executionStats.nReturned**

匹配查询条件的记录数。

**executionStats.executionTimeMillis**

包含执行计划分析和语句执行在内的总耗时，单位毫秒。

**executionStats.totalKeysExamined**

索引记录扫描数。

**executionStats.totalDocsExamined**

语句执行过程中扫描的总记录数。通常涉及记录扫描的阶段是 COLLSCAN 和 FETCH。

注意记录被扫描并不意味着记录会被返回。

**executionStats.executionStages**

最终选择的执行计划的各个阶段的执行情况。

**executionStats.executionStages.works**

语句执行阶段耗费的 “单位工作” 数，一个执行会被拆解为多个单位工作，一个单位工作可能是检验一个索引键、从集合中取一条记录等。

**executionStats.executionStages.advanced**

该阶段输出的临时结果数，也就是传递给父阶段的结果数。

**executionStats.executionStages.needYield**

阶段因为需要放弃锁而暂停执行的次数。

**executionStats.executionStages.saveState**

因为暂停执行而保存当前状态的次数。

**executionStats.executionStages.restoreState**

恢复之前暂停时状态的次数。

**executionStats.executionStages.isEOF**

是否是终止阶段。

**executionStats.executionStages.inputStage.keysExamined**

对索引检测的阶段（如 IXSCAN），keysExamined 是索引键的检索数。

**executionStats.executionStages.inputStage.docsExamined**

一个阶段中扫描的记录数。

#### [#](#queryModifications) queryModifications

包含数据库对查询语句的修改，可以更清晰感知到最终查询语句的形态。该修改只会发生在小程序端的请求中。修改规则如下：

1. 安全规则下，查询语句中的所有 `{openid}` 完整字符串会被替换为当前用户实际 openid
2. 权限选择仅创建者可读写时，查询语句的 `_openid` 字段会置为当前用户 openid

Incorrect translation.