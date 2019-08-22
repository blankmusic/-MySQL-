## -MySQL-
# 基本操作
转自
https://www.cnblogs.com/qzsoul/p/6919564.html

#  MySQL的启动和关闭
1 MySQL的启动<br>
 开始-运行 cmd- net-start-mySQL<br>
2 连接MySQL服务<br>
MySQL -uroot -p<br>
3 关闭<br>
net-stop-MySQL

# 操作数据库
```text
1 创建数据库
drop database databasename if exists
ceate database databasename;
2 查看数据库
show databases;
3 选择指定数据库
use 数据库名
4 删除数据库
drpop database stabasename;
```
# 操作数据表
```text
1 创建表
drop table tablename if exists
create table tabeName
(column_name column_type not null,..)c:\AppSerc\MySQL\data\数据库名\路径下 自动创建对应表文件

注：create table 属性说明
column_name 字段名
column_type 字段类型
Notnull|null 该列是否可以为空
Primary key 该列是否为主键
AUTO_INCREMENT 该列是否为自动编码

（表名.frm,表名.MYD,表名.MYI）


2 查看数据库中的表
show tables;
3 查看数据中所有的表
show table;(前提是前面使用use database database_name)
4 查看数据表结构
decribe table_name;
5 修改数据表结构
alter table table_name
  add [column] create_definition [first|after column_name]//添加新字段
  add primary key(index_col_name)//添加主键
  alter [colum]col_name{set default literal |rop default}//修改字段名称
  change[column] old_col_name create_definition//修改字段名称及类型
  modify[column] create_definition//修改字段类型
  drop [column]col_name//删除字段
  drop primary ky//删除主键
  rename as new_table_name//更改表名
  
  eg:alter tble Admin_info
    drop A_pwd
    rename as Admin_info2;
  6 删除指定表
  drop table table_name;
```
# 操作MySQL数据
```text
1 添加表数据

```
 
