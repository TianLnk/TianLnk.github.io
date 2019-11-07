title: SQL语句
author: 田亮
abbrlink: 48as
tags:
  - SQL
categories:
  - SQL
date: 2019-05-05 10:04:00
---
## 一些最重要的 SQL 命令
1. SELECT - 从数据库中提取数据
1. UPDATE - 更新数据库中的数据
1. DELETE - 从数据库中删除数据
1. INSERT INTO - 向数据库中插入新数据
1. CREATE DATABASE - 创建新数据库
1. ALTER DATABASE - 修改数据库
1. CREATE TABLE - 创建新表
1. ALTER TABLE - 变更（改变）数据库表
1. DROP TABLE - 删除表
1. CREATE INDEX - 创建索引（搜索键）
1. DROP INDEX - 删除索引
<!--more-->

## 基础语句
```sql
# 创建数据库
create datebase tian
# 删除数据库
drop database tian
# 使用此数据库
use tian
# 创建表
CREATE TABLE xinxi(
姓名 VARCHAR(60) NOT NULL,
年龄 CHAR NOT NULL,
性别 CHAR NOT NULL,
电话 VARCHAR(60)
);
#删除表
drop table xinxi;
#增加新的列
ALTER TABLE xinxi ADD COLUMN 其它 VARCHAR(60)
# 添加主键
primary key(姓名) #这是在创建表的同时添加
alter table xinxi add primary key(姓名)#这是创建表之后使用
# 添加索引

```
## 索引
索引就类似于中文字典前面的目录，按照拼音或部首都可以很快的定位到所要查找的字。
唯一索引（UNIQUE）：每一行的索引值都是唯一的（创建了唯一约束，系统将自动创建唯一索引）
主键索引：当创建表时指定的主键列，会自动创建主键索引，并且拥有唯一的特性。
聚集索引（CLUSTERED）：聚集索引就相当于使用字典的拼音查找，因为聚集索引存储记录是物理上连续存在的，即拼音 a 过了后面肯定是 b 一样。
非聚集索引（NONCLUSTERED）：非聚集索引就相当于使用字典的部首查找，非聚集索引是逻辑上的连续，物理存储并不连续。
PS：聚集索引一个表只能有一个，而非聚集索引一个表可以存在多个。


