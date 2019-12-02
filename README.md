# mysql—知识点总结

![mysql对比其他的数据库](../mysql知识总结/images/chapter01.jpg)

从上图可以看出mysql现在的占比例很大。

#### 为什么要学习数据库

 - 实现数据持久化
 - 使用完整的管理系统统一管理，易于查询

#### 数据库相关的概念

 - DB
    - 数据库(database):储存数据的仓库，它保存了一系列有组织的数据。
 - DBMS
    - 数据库管理系统。数据库是通过DBMS创建和操作的的容器
    - 常见的数据库管理系统Mysql，Oracle ，DB2，SqlServer等等。
 - SQL
    - 结构化程序语言：专门用来与数据库通信的语言。
    - 优点：
       - 1.不是某个数据库供应商专有的语言，几乎所有得DBMS都支持SQL
       - 简单易学
       - 是一种很强大的语言，灵活使用其语言，可以进行非常复杂和高级数据库操作。
 - 

#### 数据库存储数据的特点

 	1. 将数据放到表中，表在放到数据库中
 	2. 一个数据库可以有多个表，每个表都有一个名字，用来标识自己。表名具有唯一性。
 	3. 表具有一些特性，这一些特性定义了数据库在表中数如何存储的，类似于Java 中的类的设计。
 	4. 表由列组成，我们也成为字段，所有的表都是有一个或者多列组成的，每一列类似于Java中的属性。
 	5. 表中的数据是按行存储的，每一行类似于Java中的对象。

#### MySQL产品的特点

​	1.MySQL数据库隶属于MySQLAB公司，总部位于瑞典，后来被Oracle公司收购。

#### 优点

- 成本低，开源免费，可以免费使用。
- 性能高，执行很快
- 简单：很容易安装和使用

#### MySQL服务的启动和停止

 -  方式一：计算机---右键管理---服务
 -  方式二：通过管理员身份运行 net start 服务名(启动服务) net stop 服务名(停止服务)

#### MySQL服务的登陆和退出

 - 方式一：通过mysql自带的客户端，只限于root用户
 - 方式二：通过windows自带的客户端。登录：mysql -h 主机名 -P 端口号 -u 账户号 -p 密码

#### MySQL常见命令介绍

 - show databases; 显示当前数据库
 - use 数据库名字 ：表示使用该数据库
 - show tables ：显示当前数据库中有哪一些表
 - show tables from 数据库名字: 查看其他数据库的有哪一些表
 - select database():表示查看当前的数据库
 - desc 表名。查看当前表结构
 - select version(): 查看mysql版本号
 - mysql --version():查看mysql版本号
 - mysql -V ：查看mysql版本号

#### MySQL语法规范

 - 不区分大小写，但是建议关键字大写，表名，列名小写
 - 每条命令用分号结尾(;)
 - 每一条命令根据需要，可以换行和缩近
 - 注释。单行注释#  多行注释   /* */

#### MySQL入门

 - 初始化myemployee

   ```sql
   (```)
   	#地区表
   CREATE TABLE `locations` (
     `location_id` int(11) NOT NULL AUTO_INCREMENT,
     `street_address` varchar(40) DEFAULT NULL,
     `postal_code` varchar(12) DEFAULT NULL,
     `city` varchar(30) DEFAULT NULL,
     `state_province` varchar(25) DEFAULT NULL,
     `country_id` varchar(2) DEFAULT NULL,
     PRIMARY KEY (`location_id`)
   ) ENGINE=InnoDB AUTO_INCREMENT=3201 DEFAULT CHARSET=utf8;
   (```)
   ```



​	