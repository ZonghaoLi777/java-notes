# 数据库
* 什么是数据库  
数据库就是存储数据的仓库，其本质是一个文件系统，数据按照特定的格式将数据存储起来，用户可以对数据库中的数据进行增加，修改，删除及查询操作。  
* 什么是数据库管理系统  
数据库管理系统（DataBase Management System，DBMS）：指一种操作和管理数据库的大型软件，用于建立、使用和维护数据库，对数据库进行统一管理和控制，以保证数据库的安全性和完整性。用户通过数据库管理系统访问数据库中表内的数据。  
* 常见的数据库管理系统  
MYSQL	：开源免费的数据库，小型的数据库.已经被Oracle收购了.MySQL6.x版本也开始收费。  
Oracle	：收费的大型数据库，Oracle公司的产品。Oracle收购SUN公司，收购MYSQL。  
DB2		：IBM公司的数据库产品,收费的。常应用在银行系统中.  
SQLServer：MicroSoft 公司收费的中型的数据库。C#、.net等语言常使用。  
SyBase	：已经淡出历史舞台。提供了一个非常专业数据建模的工具PowerDesigner。  
SQLite	: 嵌入式的小型数据库，应用在手机端。  
Java相关的数据库：MYSQL，Oracle．  
这里使用MySQL数据库。MySQL中可以有多个数据库，数据库是真正存储数据的地方。  
* 数据库与数据库管理系统的关系  
![text](img/doc2801.png?raw=true)  
## 数据库表
数据库中以表为组织单位存储数据。  
表类似我们的Java类，每个字段都有对应的数据类型。  
那么用我们熟悉的java程序来与关系型数据对比，就会发现以下对应关系。  
类----------表  
类中属性----------表中字段  
对象----------记录  
## 表数据
根据表字段所规定的数据类型，我们可以向其中填入一条条的数据，而表中的每条数据类似类的实例对象。表中的一行一行的信息我们称之为记录。  
![text](img/doc2802.png?raw=true)  
* 表记录与java类对象的对应关系  
![text](img/doc2803.png?raw=true)  
# MySql数据库
## SQL语句
数据库是不认识JAVA语言的，但是我们同样要与数据库交互，这时需要使用到数据库认识的语言SQL语句，它是数据库的代码。  
结构化查询语言(Structured Query Language)简称SQL，是一种数据库查询和程序设计语言，用于存取数据以及查询、更新和管理关系数据库系统。  
创建数据库、创建数据表、向数据表中添加一条条数据信息均需要使用SQL语句。  
* SQL分类：
  + 数据定义语言：简称DDL(Data Definition Language)，用来定义数据库对象：数据库，表，列等。关键字：create，alter，drop等 
  + 数据操作语言：简称DML(Data Manipulation Language)，用来对数据库中表的记录进行更新。关键字：insert，delete，update等
  + 数据控制语言：简称DCL(Data Control Language)，用来定义数据库的访问权限和安全级别，及创建用户。
  + 数据查询语言：简称DQL(Data Query Language)，用来查询数据库中表的记录。关键字：select，from，where等
## SQL通用语法
* SQL语句可以单行或多行书写，以分号结尾
* 可使用空格和缩进来增强语句的可读性
* MySQL数据库的SQL语句不区分大小写，建议使用大写，例如：SELECT * FROM user。
* 同样可以使用/**/的方式完成注释
* MySQL中的我们常使用的数据类型如下  
![text](img/doc2804.png?raw=true)  
## 数据库操作：database
* 创建数据库
  + 格式:
    - create database 数据库名;
    - create database 数据库名 character set 字符集;
例如：  
```sql
#创建数据库 数据库中数据的编码采用的是安装数据库时指定的默认编码 utf8
CREATE DATABASE day21_1; 
#创建数据库 并指定数据库中数据的编码
CREATE DATABASE day21_2 CHARACTER SET utf8;
```
* 查看数据库
```sql
#查看数据库MySQL服务器中的所有的数据库:  
show databases;
#查看某个数据库的定义的信息:
show create database 数据库名;
```

* 删除数据库
```sql
drop database 数据库名称;
```

* 其他的数据库操作命令
```sql
#切换数据库：
use 数据库名;
```

* 查看正在使用的数据库:
```sql
select database();
```
## 表结构相关语句
* 格式:  
```sql
create table 表名(
   字段名 类型(长度) 约束,
   字段名 类型(长度) 约束
);
```
## 主键约束
主键是用于标识当前记录的字段。它的特点是非空，唯一。在开发中一般情况下主键是不具备任何含义，只是用于标识当前记录。  
* 格式:  
1.在创建表时创建主键，在字段后面加上  primary key.    
```sql
create table tablename(	
  id int primary key,
  .......
)
```
2.在创建表时创建主键，在表创建的最后来指定主键  
```sql
create table tablename(						
  id int，
  .......，
  primary key(id)
)
```
3.删除主键：alter table 表名 drop primary key;  
```sql
alter table sort drop primary key;
```
4.主键自动增长：一般主键是自增长的字段，不需要指定。  
```
实现添加自增长语句,主键字段后加auto_increment(只适用MySQL)
```
其他约束：其他约束还有如外键、唯一、非空等，会在就业班详细介绍。  

