# [#](#Database-RegExp) <Database>.RegExp

构造正则表达式，仅需在普通 js 正则表达式无法满足的情况下使用

## [#](#options-参数说明) options 参数说明

`options` 支持 i, m, s 这三个 flag，注意 JavaScript 原生正则对象构造时仅支持其中的 i, m 两个 flag，因此需要使用到 s 这个 flag 时必须使用 `db.RegExp` 构造器构造正则对象。flag 的含义见下表：

| flag | 说明 |
| --- | --- |
| i | 大小写不敏感 |
| m | 跨行匹配；让开始匹配符 `^` 或结束匹配符 `$` 时除了匹配字符串的开头和结尾外，还匹配行的开头和结尾 |
| s | 让 `.` 可以匹配包括换行符在内的所有字符 |

## [#](#基础用法示例) 基础用法示例

```
// 原生 JavaScript 对象
db.collection('todos').where({
  description: /miniprogram/i
})

// 数据库正则对象
db.collection('todos').where({
  description: db.RegExp({
    regexp: 'miniprogram',
    options: 'i',
  })
})

// 用 new 构造也是可以的
db.collection('todos').where({
  description: new db.RegExp({
    regexp: 'miniprogram',
    options: 'i',
  })
})
```

Incorrect translation.