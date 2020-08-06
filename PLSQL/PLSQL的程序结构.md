# PL/SQL 的程序结构<br>
* 声明部分<br>（必须）
* 可执行部分<br>（必须）
* 异常处理部分（非必须）<br>
# 什么是PL/SQL<br>
是SQL过程化的扩展，也就是扩展了`控制语句`，是的SQL具有程序模块结构语言的特征，包括异常处理功能。<br>
存储过程是由PL/SQL语句书写的，经编译和优化后存储在数据库服务器中的过程，他们成为SQL服务器模块，使用时只需调用即可。<br>
## 声明部分<br>
DECLARE ---变量 常亮等只能在该基本块块中使用。基本块执行结束时，定义就不再存在。<br>
### 定义变量的语法格式<br>
变量名 数据类型 notnull：=初值表达式或<br>
变量名 数据类型 notnull 初值表达式<br>
### 定义常量的语法模式
常量名 数据类型 CONSTANT：=常量表达式<br>
注：敞亮必须要给一个值，并且改制在存在期间不能改变，改变将返回异常。
### 赋值语句<br>
变量名称：=表达式<br>

## 可执行部分
```SQL
BEGIN
---SQL 语句、PL/SQL的流程控制语句
EXCEPTION
----异常处理部分
END;
```

## 异常处理部分<br>
exception这一部分是可选的，在这一部分中处理异常或错误。<br>

例：假设已经存在课程表Courses，现在要在Course表中插入10门课程信息。课程编号从0001到0010.
```SQL
//创建Course表
CREATE TABLE Course (
CNO number(4) Constraint pk_c Primary key,
Cname VARCHAR(20),
Grade number(3)
)
//使用存储过程完成插入
DECLARE
CNO NUMBER;
BEGIN
CNO:=0010;
LOOP
INSERT INTO Course(CNO) VALUES(TO_CHAR(CNO,'9999'));//SQL 语句
CNO:=CNO+1;
EXIT WHEN CNO>0010;
END LOOP;
EXCEPTION
WHEN OTHERS THEN
DBMS_OUTPUT.PUT_LINE('ERROR');
END;
```
## PL/SQL的功能<br>
- 条件控制<br>循环控制<br>错误处理

### 条件控制语句<br>
```SQL
IF cndition THEN
sequence of statementd;
END IF

IF condition 
***;
ELSE
***;
END IF;
```

### 循环控制语句<br>
```SQL
LOOP
***;
END LOOP;

WHILE condition LOOP
***；
END LOOP;

FOR count IN [REVERSE]bound1...bound2 LOOP
***;
END LOOP;

```
多数数据库服务器的PL/SQL都提供EXIT、BREAK或LEAVE等循环结束语句。<br>

## 异常处理<br>
-系统预定义异常处理<br>自定义异常处理

定义名为GRADEERROR的异常，在SC表中查找Sno等于0001的记录，<br>
将他的成绩存入变量tempGrade中，判断tempGrade值，若不在0和100之间，<br>
说明该学生的成绩值有问题，则激活异常处理，显示相应的提示信息。<br>
```SQL
SET SERVEROUTPUT ON 
DECLARE
GRADEERROR EXCEPTION;
tempGrade NUMBER;
BEGIN
SELECT GRADE INTO tempGrade
FROM SC
WHERE Sno='0001';
IF tempGrade<0OR tempGrade>100THEN 
RAISE GRADEERROR;
END IF;
EXCPTION
WHENGRADEERROR THEN
DBMS_OUTPUT.PUT_LINE('成绩超出范围');
END;
```

## 存储过程的优点 <br>
保存了PL/SQL语句的书写过程，编译优化后存储在数据库服务器中，使用时调用即可。<br>
* 运行效率高<br>
* 降低了客户机和服务器之间的通信量<br>
* 方便实施企业规划<br>

### 存储过程的用户接口<br>
创建存储过程、执行存储过程、删除存储过程

### 创建存储过程<br>
```SQL
CREATE Procedure 过程名（参数1，参数2，。。。）
AS
<PL/SQL块>;
```
* 过程名：数据库服务器合法的对象标识

* 参数列表：必须指定数据类型

* 过程体：一个<PL/SQL块>，包括声明和可执行语句部分
ALTER Procedure 过程名1 RENAME TO 过程名2： 
### 执行存储过程

CALL.PERFORM Procedure 过程名（[参数列表]）;

### 删除存储过程<br>
DROP PROCEDURE 过程名();

## 触发器
创建触发器，实现当在STUDENT表中删除记录<br>
后，显示表中还有几条记录的信息。<br>
```SQL
CREATE OR REPLACE TRIGGER student_count
AFTER DELETE ON student
DECLARE
cou INTEGER;
BEGIN
SELECT COUNT(*) INTO cou FROM student;
DBMS_OUTPUT.PUT_LINE(' Student table now have ' ||
cou || ' student.');
END;
/
```
