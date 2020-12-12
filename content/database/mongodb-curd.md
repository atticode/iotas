+++
title = "Mongodb Curd"
date = 2020-12-12T14:15:22+08:00
tags = []
categories = []
isCJKLanguage = true
description = ""
weight = 10
+++


## Query Documents

|  Operators  |说明 |
|------------|------|
|$lt| 小于|
|$lte|  小于等于|
|$gt| 大于|
|$gte|  大于等于|
|$ne| 不等于|
|$in | 一个键对应多个值 |
|$nin| 同上取反, 一个键不对应指定值|
|$or | 多个条件匹配, 可以嵌套 $in 使用|
|$not|  同上取反, 查询与特定模式不匹配的文档|

``` js
// e.g. : { <field1>: { <operator1>: <value1> }, ... }
// $in
db.inventory.find( { status: { $in: [ "A", "D" ] } } )
// $or
db.inventory.find( { $or: [ { status: "A" }, { qty: { $lt: 30 } } ] } )

```
