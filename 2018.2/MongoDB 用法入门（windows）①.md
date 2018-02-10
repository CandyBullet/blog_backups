[^_^]: # ( -*- coding: utf-8 -*-)
[^_^]: # ( @Author: yang zhou)
[^_^]: # ( @Date:   2018-02-10 12:33:00)
[^_^]: # ( @Last modified by:   yang zhou)
[^_^]: # ( @Last Modified time: 2018-02-10 12:33:25)

# MongoDB 用法入门（windows）① #

## 概述 ##
大家对数据库肯定不陌生，肯定也有很多人用过`MySQL`，但是在用`MySQL`的时候各种建表，写表之间的关联让人非常头疼。

`MongoDB`也是一种数据库，但是它不是用表，而是用集合来装数据的，我对这种数据储存方式很感兴趣。所以我**根据MongoDB3.6的官方说明文档**整理了`MongoDB`入门级用法，供自己开发时参考，相信对其他人也有用。

这是慕课网上MongoDB的课程：[mongoDB入门篇][1]

这是MongoDB官方说明文档：[The MongoDB Manual][2]

### 什么是MongoDB ###

`Mongodb`是面向文档数据库(Document Oriented Databases)，同时，它也是“`NoSQL`数据库”。

它非常容易扩展，并且速度很快。

### MongoDB的安装 ###

1.去mongodb的官网[http://www.mongodb.org/downloads][3]下载msi安装包（CommunityServer版本）。安装的默认路径是：`C:\Program Files\MongoDB\Server\3.6\bin`

2.为了启动mongodb方便，将mongod.exe路径加入环境变量。电脑->属性->高级系统设置->环境变量,在path里加入默认路径：`C:\Program Files\MongoDB\Server\3.6\bin`

3.在D盘新建一个mongodb文件夹用来放数据文件，并在mongodb文件夹下建立data,logs文件夹，在logs文件夹下建立mongodb.log文件

4.以**管理员**启动cmd，并且输入：`mongod --dbpath D:\mongodb\data\ --logpath D:\mongodb\logs\mongodb.log --install --serviceName"MongoDB"`

5.以**管理员**启动cmd，`net start mongodb`启动mongodb服务；`mongo 127.0.0.1:27017`进入mongo数据库；`net stop MongoDB`关闭mongodb服务

### 数据库操作 ###
1.创建并进入数据库

> use DATABASE_NAME

创建名字为TEST的数据库，并进入数据库；如果数据库已存在，则直接进入数据库。

```
use TEST
```

2.显示数据库。

> show dbs

显示所有数据库

```
show dbs
```

3.删除数据库

> db.dropDatabase()

删除TEST数据库

```
use TEST
db.dropDatabase()
```

### 集合操作 ###
1.创建集合

> db.createCollection(name, options)

创建集合名imooc的数据库

```
db.createCollection("imooc")
```

2.查看集合。

> show collections

查看所有集合
```
show collections
```
3.删除集合

> db.COLLECTION_NAME.drop()

删除集合imooc

```
db.imooc.drop()
```

### 数据操作 ###
1.create操作

> db.collection.insertOne()
> db.collection.insertMany()
> db.collection.insert()  

写入单条和多条数据：
```
db.inventory.insertOne(
   { item: "canvas", qty: 100, tags: ["cotton"], size: { h: 28, w: 35.5, uom: "cm" } }
)
db.inventory.insertMany([
   { item: "journal", qty: 25, tags: ["blank", "red"], size: { h: 14, w: 21, uom: "cm" } },
   { item: "mat", qty: 85, tags: ["gray"], size: { h: 27.9, w: 35.5, uom: "cm" } },
   { item: "mousepad", qty: 25, tags: ["gel", "blue"], size: { h: 19, w: 22.85, uom: "cm" } }
])
```

2.Read操作

> db.collection.find()

查找status为"D"的数据，并且显示5条。
```
db.inventory.find( { status: "D" } ).limit(5)
```
查找status为"D"的数据，并且以格式化显示。
```
db.inventory.find( { status: "D" } ).pretty()
```
查找status为"A"或"D"的数据。
```
db.inventory.find( { status: { $in: [ "A", "D" ] } } )
```
查找status为"A"并且qty为30的数据。
```
db.inventory.find( { status: "A", qty: 30} )
```
查找status为"A"或者qty为30的数据。
```
db.inventory.find( { $or: [ { status: "A" }, { qty:30 } ] } )
```
查找status为"A"的第二条数据。
```
db.inventory.find( { "status.1":  "A" } )
```
查找instock属性中qty为20的数据。（instock属性是一个集合）
```
db.inventory.find( { 'instock.qty': 20 } )
```
查找instock属性中qty为20的第一条数据。（instock属性是一个集合）
```
db.inventory.find( { 'instock.0.qty': 20 } )
```
查找status为"A"的数据，并且只返回_id,item和status字段
```
db.inventory.find( { status: "A" }, { item: 1, status: 1 } )
```
查找status为"A"的数据，并且只返回item字段，不返回status和_id字段

```
db.inventory.find( { status: "A" }, { item: 1, status: 0, _id: 0 } )
```
查找status为"A"的数据，并且只返回_id和item字段，以及size字段的uom属性
```
db.inventory.find({ status: "A" }, { item: 1, "size.uom": 1 })
```
查找item为null或者不存在item属性的数据

```
db.inventory.find( { item: null } )
```
查找item属性为null的数据

```
db.inventory.find( { item : { $type: 10 } } )
```
查找不存在item属性的数据

```
db.inventory.find( { item : { $exists: false } } )
```
相当于db.users.find( { type: 2 } )，因为结果返回一个循环指针
```
var myCursor = db.users.find( { type: 2 } );
myCursor
```

3.Update操作 

> db.collection.updateOne()
> db.collection.updateMany()
> db.collection.replaceOne()
> db.collection.update()

将item为"paper"的第一条数据的size.uom改为"cm"，status改为"P"
```
db.inventory.updateOne(
   { item: "paper" },
   {
     $set: { "size.uom": "cm", status: "P" },
   }
)
```
将item为"paper"的所有数据的size.uom改为"cm"，status改为"P"
```
db.inventory.updateMany(
   { item: "paper" },
   {
     $set: { "size.uom": "cm", status: "P" },
   }
)
```
把item为"paper"的第一个数据替换为后一个数据

```
db.inventory.replaceOne(
   { item: "paper" },
   { item: "paper", instock: [ { warehouse: "A", qty: 60 }, { warehouse: "B", qty: 40 } ] }
)
```
4.delete操作

> db.collection.deleteOne() 
> db.collection.deleteMany()
> db.collection.remove()

删除第一个status为"D"的数据；删除所有status为"D"的数据

```
db.inventory.deleteOne( { status: "D" } )
db.inventory.deleteMany( { status: "D" } )
```

  [1]: http://www.imooc.com/learn/295
  [2]: https://docs.mongodb.com/manual/
  [3]: http://www.mongodb.org/downloads
