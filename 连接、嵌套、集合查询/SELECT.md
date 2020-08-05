# 连接查询<br>
```text
有时候用户查询可能涉及多个表，才能查出所需要的的信息。
1、如果一个查询需要对多个表进行操作，就称为连接查询。
2、连接查询可以在SELCT语句的FROM子句或WHERE子句中建立。不同的子句有不同的分类方式。
```
* WHERE子句连接的查询<br>
>> 等值连接查询<br>非等值连接查询<br>自然连接查询<br>外部连接查询<br>复合条件连接查询<br>

* FROM子句连接的查询<br>
>> 内连接<br>外连接<br>交叉连接

## WHERE子句中的连接查询
* 等值连接和非等值连接<br>
```text
连接查询的WHERE子句中用来连接两个表的条件称为连接条件或连接谓词,一般格式为
tablename1.col1 比较运算符 tablename2.col2
其中比较运算符主要有：= > < >= <= !=
此外连接条件还可以如下所示：
tablename1.col1 BETWEEN tablename2.col2 AND tablename2.col3
```
*当连接运算符为=时，称为等值连接。其他运算符非等值连接。<br>
*连接条件中的列名为连接字段。连接字段类型必须是可比的，但不必相同。<br>
eg：查询每个学生及其选修课程的情况<br>
```SQL
SELECT * FROM Student,SC WHERE Student.sno=SC.sno;
```
连接运算中有两种特殊情况<br>
* 笛卡尔积连接<br>
* 自然连接<br>
eg：Course表盒SC表做笛卡尔积连接
```SQL
SELECT * FROM Course,SC;
```
如果按照两个表中的相同属性进行连接，且去除了目标列中重复属性的列，但保留了`所有`不重复的属性列<br>
则称为自然连接。<br>
eg：Course表和SC表做自然连接
```SQL
SELECT Course.Cno,Cname，Cpno,Ccredit,Sno,Grade
FROM Course,SC
WHERE Course.Cno=SC.Cno;
```
连接操作还可以是表自身的连接，称为表的自身连接。
eg：查询每一门课的间接先修课（即先修课的先修课）
```SQL
SELECT FIRST.Cno, SECOND. Cpno
FROM Course FIRST, Course SECOND
WHERE FIRST. Cpno =SECOND.Cno;
```
例以Student表为主体列出每个学生的基本
情况及其选课情况。
```SQL
SELECT Student.Sno, Sname, Ssex, Sage,
Sdept, Cno, Grade
FROM Student, SC
WHERE Student.Sno=SC.Sno(+);
```
* 上面各个连接查询中，WHERE子句中只有一个条件，即用于连接两个表的谓词。WHERE子句中有多个条件的连接操作，称为复合条件连接。<br>
例:查询选修2号课程且成绩在90分以上的所有学生。
```SQL
SELECT Student.Sno, Sname
FROM Student, SC
WHERE Student.Sno=SC.Sno AND
SC.Cno=2 AND SC.Grade>90;
```
## FROM子句中的连接查询<br>
连接格式：FROM join_table join_type join_table 　[ON (join_condition)]<br>
* join_table:参与连接操作的表名.连接可以对同一个表操作，也可以对多表操作，对同一个表操作的连接又称做自连接。<br>
* join_type:连接类型，可分为三种：内连接、外连接和交叉连接。<br>
>> 内连接(INNER JOIN) 使用比较运算符进行表间某
(些)列数据的比较操作，并列出这些表中与连接
条件相匹配的数据行。根据所使用的比较方式不
同，内连接又分为等值连接、自然连接和不等连
接三种。
>> 外连接分为左外连接(LEFT OUTER JOIN或
LEFT JOIN)、右外连接(RIGHT OUTER JOIN或
RIGHT JOIN)和全外连接(FULL OUTER JOIN或
FULL JOIN)三种。与内连接不同的是，外连接不
只列出与连接条件相匹配的行，而是列出左表(左
外连接时)、右表(右外连接时)或两个表(全外连接
时)中所有符合搜索条件的数据行。
>> 交叉连接(CROSS JOIN)没有ON子句，它
返回连接表中所有数据行的笛卡尔积，其
结果集合中的数据行数等于第一个表中符
合查询条件的数据行数乘以第二个表中符
合查询条件的数据行数。
>> 连接操作中的ON (join_condition) 子句指
出连接条件，它由被连接表中的列和比较
运算符、逻辑运算符等构成。
