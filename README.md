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
`;
    
  6 删除指定表
  drop table table_name;
```
# 操作MySQL数据
```text
1 添加表数据
语法1 ：insert into table_name values(val1,val2,...)(autoincrement=null)
语法2 ：insert into table_name (字段1， 字段2，...) values(val1,val2,...)
语法3 ：insert into table_name set 字段1=val1，字段2=val2，字段3=val3，...
2 更新表数据
update table_name set 字段1=值1 where 查询条件
若无查询条件，其中所有的数据行都会被修改

3 删除表数据
delet from table_name where 查询条件

4 查询表数据
select* from table_name;

5 限制查询记录数
select *from table_name limit[statr] offset[length]
start:表示从第几行开始输出，0表示第一行
offset:表示输出几行

```
# 数据模型
 ## 概念模型--实体-联系方法（E-R模型）
 ```text
 E-R:概念模型的一种表示方法。
     实体型：用矩形表示，在矩形框内写明实体名。
     属性：用椭圆表示，无向边连接实体。
 联系
    联系本身：用菱形表示。框内写明联系名，并用无向边分别与有关实体连接起来，并在无向边旁标注联系的
类型（1:1、1：n、m：n）。
 设计E-R模型的三条设计原则
  1、相对原则：关系 实体 属性 联系等，是对同一对象抽象过程的不同解释和理解，设计过程实际上是一个对
对象的抽象过程。抽象结果可能不同。
  2、一致原则：同一对象在不同业务系统的抽象结果要求保持一致。业务系统是指建立系统的各子系统。
  3、简单原则：魏建华E-R模型，先世界的食物能作为属性对待的，进行归结为属性处理。
属性和实体之间并无一定的界限。
属性的两个条件：
  1、属性不再具有需要描述的性质，即属性在含义上是不可分的数据项。
  2、属性不能在与其他实体集具有联系，即E-R模型指定联系只能是实体集之间的联系、
建立E-R图：
  1、确定实体类型
  2、确定联系类型
  3、把实体类型和联系类型组合成E-R图
  4、确定实体类型和联系类型的属性。
 ```
 ## 逻辑模型--信息模型
 ```text
 信息模型：是按计算机系统的观点对数据进行建模，直接面向数据库的逻辑结构，与计算机系统和DBMS
（支持某种数据模型）相关，有严格的形式化定义
 （层级、网状和关系模型），以便于在计算机系统中实现。
   网状模型、层次模型
   关系模型、面向对象模型等。
 ```
 ## 物理模型
 ```text
 物理模型是对数据最底层的抽象，描述数据在系统内部的表示方式和存取方法。磁盘磁带、
 ```
 ## 数据模型的组成要素
 ```text
 组成要素：
   数据结构
   数据操作
   完整性约束条件
 数据结构： 描述数据库的组成对象，以及对象之间的联系。
 按照数据结构的类型命名数据模型（层次模型、网状模型、关系模型）
 数据操作：对数据库中各种对象和实例允许只想的操作的集合和有关的操作规则。
 数据操作的类型：
   查询
   更新（插入 删除 修改）
 数据完整性约束条件：
   一组完整性规则的集合。
   是给定的数据模型中数据及其联系所具有制约和依存规则，用以限定符合数据模型的数据库状态以及
   状态的变化，以保证数据的正确有效相容。
 常用的几种数据模型：
   非关系模型：层次模型（Hierarchical Model）、 网状模型（network model）
   关系模型（Relational Model）
   面向对象模型
 层次模型的数据结构（树）--一对多
   层次模型的数据操作：查询 插入 删除 更新
   层次模型的优点： 数据结构简单
                   查询效率高于关系模型，不低于网状模型
                   良好的完整性支持
             缺点： 多对多联系表示不自然
                    对插入删除操作的限制多，应用程序编写较复杂
                    查询子女结点必须通过双亲结点
                    结构严密，层次命令趋于程序化
网状结构：网状数据库系统采用网状结构作为数据的组织方式。
  代表的系统 DBTG系统，奠定了数据库系统的基本概念、方法技术。
  实际系统：Cullinet Software Inc.公司的IDMS
  满足下面两个条件的基本层次联系的集合：
     1、允许一个以上的节点无双亲结点
     2、一个节点可以有多个双亲结点也可以有多个子女节点
     3、有向图中的节点是记录类型，1：n。箭尾是双亲结点，箭首是子女节点
  表示方法：
    实体性：记录类型表述
    属性：字段描述
    联系：节点之间的连线表示记录类型之间的`一对多的父子联系`
 网状数据结构的优点：更新操作简单，查询可以有多种方法实现
                   存取效率较高
              缺点：结构复杂，不利于最终用户掌握
                    DDL、DML语言犊砸，用户不容易使用。
 关系模型
   关系数据库系统采用关系模型作为数据的组织方式。
   在用户观点下，关系模型中的数据是一张二维表，由行和列组成。
       关系（Relation）--一个关系对应通常说的一张表
       元组（Tuple）--表中的一行即为一个元祖
       属性（Attribute）--表中的一列为一个属性，列名即为属性名。
    关系模型中的实体和实体之间的联系都是用关系来表示。
    eg1：学生和系之间的一对多的联系
        学生（学号，姓名，年龄，性别，系号，年级）
        系（系号，系名，办公地点）
     eg2: 系和系主任一对一的联系
          系（系号，系名，办公地点）
          系主任（系号，系主任姓名）
     eg3: 学生与课程之间的`对多联系`
          学生（学号，姓名，年龄，性别，系号，年级）
          课程（课程号，课程名，学分）
          选修（学号，课程号，成绩）
   关系必须是规范化的，妈祖一定的规范条件
      最基本的规范条件：关系的每一个分量必须是一个不可分可的数据项，即，`不允许表中还有表`      
 
 ```
