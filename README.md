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
 ```
最基本的规范条件：关系的每一个分量必须是一个不可分可的数据项，即，`不允许表中还有表` 。
术语对比
关系术语|一般表格术语
-----|-----
关系名|表名
关系模式|表头（表格的描述）
关系|（一张）二维表
元组|记录或行
属性|列
属性名|列名
属性值|列值
分量|一条记录中的一个列值
非规范关系|表中有表（大表中有小表）
```text
数据操作：
        集合操作，操作对象和操作结果都是关系--若干元组的集合
            查询 插入 删除 更新
        存储路径对用户隐蔽，用户在要指出干什么，不必详细说明怎么干
关系的完整性约束：
        实体完整性
        参照完整性
        用户定义完整性
关系数据模型的优点
        建立在严格的数学概念机出航
        概念单一 实体和各类联系都用关系来表示，对数据的检索结果也是关系
        关系模型的存取路径对用户透明
             缺点：
             存取路径对用户透明导致查询效率不如非关系型数据模型
             为了提高性能，必须对用户的查询语句进行优化，增加了开发DBMS的难度。        
面向对象的数据模型
   面向对象的数据模型（Object-Oriented Data Model简称OO数据模型）是面向对象程序设计方法
   与数据库技术相结合的产物，用以支持非传统应用领域对数据模型提出的新需求
 基本的结构是对象而不是记录，一切事物概念都可以看做对象。对象包括描述它的数据和对它操作的方法的定义。
 它是一种可以扩充的数据模型，用户可以根据应用需要定义新的数据类型以及相应的约束和操作。
```
### 面相对象的数据模型和关系数据模型比较
>> * 在关系数据模型中基本数据结构是表，这相当于面向对象数据模型中的类（类中包括方法），<br>
关系中的数据元组相当于面向对象数据模型中的实例（实例中包括方法）<br>
>> * 在关系数据模型中，但对数据库的操作都对结尾对关系的云端，在面向对象数据模型中对类层次<br>
的操作分为两部分：封装在类内的操作即方法，雷志坚相互沟通的操作即消息。<br>
>> * 在关系数据模型中有域、实体和参照完整性约束，完整性约束条件可以用逻辑公式表示，称为完整性约束方法。<br>
在面向对象的数据模型中这月约束公式可以用方法或者消息表示，称为完整性约束消息。<br>
>> * 面向对象数据模型具有封装性 信息隐匿性 持久性 数据模型可扩充性 继承性 代码共享和软件重用性等特性，<br>
并有丰富的寓意便于更自然的描述现实世界。<br>
# 关系型数据库<br>
## 域<br>
域：是一组具有相同数据类型 的值的集合。<br>
整数<br>实数<br>介于某个取值范围的整数<br>长度指定长度的字符串集合<br>{'男'，‘女’}<br>
## 码<br>
```text
候选码（Candidate Key）
   若关系中的某一属性组的值能唯一的表示一个元组，则称该属性组为候选码
   简单的情况：候选码只包含一个属性
全码（All-Key）
   最极端的情况：关系模式的所有属性组是这个关系模式的候选码，称为全码（ALL-Key）。
主码
   若一个关系有多个候选码，则选定其中一个为主码（Primary Key）
主属性
   候选码的诸属性称为主属性(Prime attribute)
   不包含在任何候选码中的属性成为非主属性（Non-Prime attribute）或非码属性（No-key attribute）
```
## 关系的三类完整性约束<br>
>> 实体完整性<br>参照完整性<br>用户定义完整性<br>
实体完整性和和参照对应完整性约束条件是关系的两个不变性，应该由关系系统自动支持。<br>
用户定义的完整性是应用领域需要遵循的约束条件，体现了具体领域中的语义约束。<br>
### 实体完整性规则（Entity Integrity）
* 若属性A是基本关系R的诸属性，则属性A不能取空值<br>
eg: Student(·Sno·,Sname,SSex,Sage,Sdept)，Sno为主属性，不能为空值<br>
```text
实体完整性规则说明：1 实体完整性规则是针对基本关系而言。一个基本关系表通常对应现实世界的一个实体集。
2 现实世界中的实体时刻区分，即他们具有某种唯一的标识。
3 关系模型中以主码作为唯一的标识。
4 主码中的属性即主属性不能取空值。主属性null，就说明存在某个不可标识的实体，即存在不可区分的实体。这与第二句矛盾，因此
这个规则称为实体完整性。
```
### 参照完整性
* 关系间的引用
* 外码
* 参照完整性规则
#### 关系间的引用
在关系模型中实体及是实体间的联系都是用关系来描述的，因此可能存在着关系与关系间的引用。<br>
学生实体：学生(学号，姓名，性别，`专业号`，年龄)<br>
专业实体：专业（`专业号`，专业名）<br>学生关系引用了专业关系的主码--专业号，学生关系中的专业号的值必须是存在的专业的专业号，即专业。<br>
#### 外码
学生关系的专业号与专业关系的主码，专业号相对应。专业号属性是学生关系的外码，专业关系是被参照的关系，学生关系为参照关系。<br>
班长与本身的主码学号相对应--班长是外码，学生关系是参照关系也是被参照关系。
#### 参照关系完整性规则
若属性或属性组F是基本关系R的外码，它与基本关系S的主码Ks相对应（基本关系R和S不一定是不同的关系），则对于R中每个元组在F上的值必须为：<br>
* null(F的每个属性值均为空值)
* 等于S中某个元组的主码值
### 用户定义完整性
针对某一具体关系数据库的约束条件，反应某一具体应用所涉及的数据必须满足的语义要求。<br>
例子：课程（课程号，课程名，学分）：课程号属性必须为唯一值，非主属性课程名不能取空值。学分只能取{1,2,3,4}
# 数据库系统-关系数据库标准语言SQL
知识要点：<br>
* SQL概述
* 数据定义
* 数据查询
* 数据更新
* 视图
## SQL概述
结构化查询语言（Structured Query Language）SQL是一种结余关系代数和关系盐酸之间的语言，功能有查询、曹总、定义、控制四个方面，是一个<br>
通用功能及其强的关系数据库标准语言。
### SQL数据库的体系结构和传统的关系模型的不同<br>
SQL|传统关系模型术语
-----|-----
外模式|视图和部分基本表
模式|基本表 元组（行）属性（列）
内模式|存储文件
### SQL的组成
* 数据操作语言（DML）：查询 插入 删除 修改
* 数据定义语言（DDL）：表的创建删除和在修改；视图和索引的创建删除。完整性约束可定义在表上。可以在创建表的时候定义约束也可以在创建后。
* 数据控制语言（DCL）：该SQL语句的目标是管理用户对数据库对象的访问。
SQL功能极强，完成核心功能只用了九个动词<br>
SQL功能|动词
----|-----
数据查询|SELECT
数据定义|CREATE，DROP，ALTER
数据操纵|INSERT，UPDATE，DELETE
数据控制|GRANT，REVOKE
eg：学生-课程模式S-T<br>
学生表：Student(Sno,Sname,Ssex,Sage,Sdept（专业）)<br>
课程表：Course(Cno,Cname,Cpno(先序课),Ccredit（学分）)<br>
学生选课表：sc(Sno,Cno,Grade（成绩）)<br>
## 数据定义
SQL数据定义语句
操作对象|操作方式
----
