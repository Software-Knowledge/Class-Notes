<!-- TOC -->

- [1. 数据库定义](#1-数据库定义)
- [2. RDBMS](#2-rdbms)
  - [2.1. RDMBS术语](#21-rdmbs术语)

<!-- /TOC -->
# 1. 数据库定义
数据库是按照数据结构来组织、存储和管理数据的仓库。  

# 2. RDBMS
1. 我们使用*关系型数据库管理系统(RDBMS)*来存储和管理大量数据。
>1. 数据以表格形式出现
>2. 每行为各种记录名称
>3. 每列为记录名称所对应的数据域
>4. 许多行和列构成一张表
>5. 若干的表单组成database

## 2.1. RDMBS术语
术语|解释
--|--
数据库|一些关联表的集合
数据表|表示数据的矩阵
列|包含有相同的数据
行|是一组相关的数据
冗余|存储两倍的信息，降低了性能，但提高了数据的安全性
主键|唯一性，一个数据表中只能包含一个主键，可以用于查询数据
外键|用于关联两个表
复合键|将多个列为一个索引键，常用于复合索引
索引|用于快速访问数据库表中的特定信息
参照完整性|要求关系中不允许引用不存在的实体
表头|每一列的名称
列|具有相同数据类型的数据的集合
行|用于描述某条记录的具体信息
值|行的具体信息，每个键必须与该列的数据类型相同
键|键的值在当前列中具有唯一性