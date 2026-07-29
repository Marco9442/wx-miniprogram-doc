开发者资源/SDK 文档/数据库/Command/聚合操作符 $/日期操作符/year/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/database/command/aggregate/AggregateCommand.year.html\#AggregateCommand-year-value-Expression-string-Object) [AggregateCommand](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/database/command/aggregate/AggregateCommand).year(value: [Expression](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/database/aggregate/Expression) ): Object
> 支持端： [小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference/changelog-server-sdk), [Web](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference/changelog-web-sdk)
聚合操作符。返回日期字段对应的年份。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/database/command/aggregate/AggregateCommand.year.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/database/command/aggregate/AggregateCommand.year.html\#value-Expression-string) value: [Expression](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/database/aggregate/Expression) 
日期字段
## [\#](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/database/command/aggregate/AggregateCommand.year.html\#%E8%BF%94%E5%9B%9E%E5%80%BC) 返回值
### [\#](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/database/command/aggregate/AggregateCommand.year.html\#Object) Object
## [\#](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/database/command/aggregate/AggregateCommand.year.html\#API-%E8%AF%B4%E6%98%8E) API 说明
语法如下：
```text
db.command.aggregate.year(<日期字段>)
```
## [\#](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/reference-sdk-api/database/command/aggregate/AggregateCommand.year.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
假设集合 `dates` 有以下文档：
```json
{
"\_id": 1,
"date": ISODate("2019-05-14T09:38:51.686Z")
}
```
我们使用 `year()` 对 `date` 字段进行投影，获取对应的年份：
```javascript
const $ = db.command.aggregate
db
.collection('dates')
.aggregate()
.project({
\_id: 0,
year: $.year('$date')
})
.end()
```
输出如下：
```json
{
"year": 2019
}
```