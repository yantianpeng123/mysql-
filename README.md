##mysql—知识点总结

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
     `location_id` int(11) NOT NULL AUTO_INCREMENT, #位置编号
     `street_address` varchar(40) DEFAULT NULL,#街道
     `postal_code` varchar(12) DEFAULT NULL,#邮编
     `city` varchar(30) DEFAULT NULL,#城市
     `state_province` varchar(25) DEFAULT NULL,#省
     `country_id` varchar(2) DEFAULT NULL,#区县
     PRIMARY KEY (`location_id`)
   ) ENGINE=InnoDB AUTO_INCREMENT=3201 DEFAULT CHARSET=utf8;
   
   insert  into `locations`(`location_id`,`street_address`,`postal_code`,`city`,`state_province`,`country_id`) values (1000,'1297 Via Cola di Rie','00989','Roma',NULL,'IT'),(1100,'93091 Calle della Testa','10934','Venice',NULL,'IT'),(1200,'2017 Shinjuku-ku','1689','Tokyo','Tokyo Prefecture','JP'),(1300,'9450 Kamiya-cho','6823','Hiroshima',NULL,'JP'),(1400,'2014 Jabberwocky Rd','26192','Southlake','Texas','US'),(1500,'2011 Interiors Blvd','99236','South San Francisco','California','US'),(1600,'2007 Zagora St','50090','South Brunswick','New Jersey','US'),(1700,'2004 Charade Rd','98199','Seattle','Washington','US'),(1800,'147 Spadina Ave','M5V 2L7','Toronto','Ontario','CA'),(1900,'6092 Boxwood St','YSW 9T2','Whitehorse','Yukon','CA'),(2000,'40-5-12 Laogianggen','190518','Beijing',NULL,'CN'),(2100,'1298 Vileparle (E)','490231','Bombay','Maharashtra','IN'),(2200,'12-98 Victoria Street','2901','Sydney','New South Wales','AU'),(2300,'198 Clementi North','540198','Singapore',NULL,'SG'),(2400,'8204 Arthur St',NULL,'London',NULL,'UK'),(2500,'Magdalen Centre, The Oxford Science Park','OX9 9ZB','Oxford','Oxford','UK'),(2600,'9702 Chester Road','09629850293','Stretford','Manchester','UK'),(2700,'Schwanthalerstr. 7031','80925','Munich','Bavaria','DE'),(2800,'Rua Frei Caneca 1360 ','01307-002','Sao Paulo','Sao Paulo','BR'),(2900,'20 Rue des Corps-Saints','1730','Geneva','Geneve','CH'),(3000,'Murtenstrasse 921','3095','Bern','BE','CH'),(3100,'Pieter Breughelstraat 837','3029SK','Utrecht','Utrecht','NL'),(3200,'Mariano Escobedo 9991','11932','Mexico City','Distrito Federal,','MX');
   
   #工种表
   CREATE TABLE `jobs` (
     `job_id` varchar(10) NOT NULL,#工种编号
     `job_title` varchar(35) DEFAULT NULL,工种名称
     `min_salary` int(6) DEFAULT NULL,#最低工资
     `max_salary` int(6) DEFAULT NULL,#最高工资
     PRIMARY KEY (`job_id`)
   ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   
   insert  into `jobs`(`job_id`,`job_title`,`min_salary`,`max_salary`) values ('AC_ACCOUNT','Public Accountant',4200,9000),('AC_MGR','Accounting Manager',8200,16000),('AD_ASST','Administration Assistant',3000,6000),('AD_PRES','President',20000,40000),('AD_VP','Administration Vice President',15000,30000),('FI_ACCOUNT','Accountant',4200,9000),('FI_MGR','Finance Manager',8200,16000),('HR_REP','Human Resources Representative',4000,9000),('IT_PROG','Programmer',4000,10000),('MK_MAN','Marketing Manager',9000,15000),('MK_REP','Marketing Representative',4000,9000),('PR_REP','Public Relations Representative',4500,10500),('PU_CLERK','Purchasing Clerk',2500,5500),('PU_MAN','Purchasing Manager',8000,15000),('SA_MAN','Sales Manager',10000,20000),('SA_REP','Sales Representative',6000,12000),('SH_CLERK','Shipping Clerk',2500,5500),('ST_CLERK','Stock Clerk',2000,5000),('ST_MAN','Stock Manager',5500,8500);
   
   
   #员工信息表
   CREATE TABLE `employees` (
     `employee_id` int(6) NOT NULL AUTO_INCREMENT, #员工编号
     `first_name` varchar(20) DEFAULT NULL,   #员工名字
     `last_name` varchar(25) DEFAULT NULL,#员工姓
     `email` varchar(25) DEFAULT NULL,#员工的邮箱
     `phone_number` varchar(20) DEFAULT NULL,#员工电话
     `job_id` varchar(10) DEFAULT NULL,#工种编号
     `salary` double(10,2) DEFAULT NULL,#月薪
     `commission_pct` double(4,2) DEFAULT NULL,#奖金率
     `manager_id` int(6) DEFAULT NULL,#上司的员工编号
     `department_id` int(4) DEFAULT NULL,部门编号
     `hiredate` datetime DEFAULT NULL,#入职时间
     PRIMARY KEY (`employee_id`),
     KEY `dept_id_fk` (`department_id`),
     KEY `job_id_fk` (`job_id`),
     CONSTRAINT `dept_id_fk` FOREIGN KEY (`department_id`) REFERENCES `departments` (`department_id`),
     CONSTRAINT `job_id_fk` FOREIGN KEY (`job_id`) REFERENCES `jobs` (`job_id`)
   ) ENGINE=InnoDB AUTO_INCREMENT=207 DEFAULT CHARSET=utf8;
   
   insert  into `employees`(`employee_id`,`first_name`,`last_name`,`email`,`phone_number`,`job_id`,`salary`,`commission_pct`,`manager_id`,`department_id`,`hiredate`) values (100,'Steven','K_ing','SKING','515.123.4567','AD_PRES',24000.00,NULL,NULL,90,'1992-04-03 00:00:00'),(101,'Neena','Kochhar','NKOCHHAR','515.123.4568','AD_VP',17000.00,NULL,100,90,'1992-04-03 00:00:00'),(102,'Lex','De Haan','LDEHAAN','515.123.4569','AD_VP',17000.00,NULL,100,90,'1992-04-03 00:00:00'),(103,'Alexander','Hunold','AHUNOLD','590.423.4567','IT_PROG',9000.00,NULL,102,60,'1992-04-03 00:00:00'),(104,'Bruce','Ernst','BERNST','590.423.4568','IT_PROG',6000.00,NULL,103,60,'1992-04-03 00:00:00'),(105,'David','Austin','DAUSTIN','590.423.4569','IT_PROG',4800.00,NULL,103,60,'1998-03-03 00:00:00'),(106,'Valli','Pataballa','VPATABAL','590.423.4560','IT_PROG',4800.00,NULL,103,60,'1998-03-03 00:00:00'),(107,'Diana','Lorentz','DLORENTZ','590.423.5567','IT_PROG',4200.00,NULL,103,60,'1998-03-03 00:00:00'),(108,'Nancy','Greenberg','NGREENBE','515.124.4569','FI_MGR',12000.00,NULL,101,100,'1998-03-03 00:00:00'),(109,'Daniel','Faviet','DFAVIET','515.124.4169','FI_ACCOUNT',9000.00,NULL,108,100,'1998-03-03 00:00:00'),(110,'John','Chen','JCHEN','515.124.4269','FI_ACCOUNT',8200.00,NULL,108,100,'2000-09-09 00:00:00'),(111,'Ismael','Sciarra','ISCIARRA','515.124.4369','FI_ACCOUNT',7700.00,NULL,108,100,'2000-09-09 00:00:00'),(112,'Jose Manuel','Urman','JMURMAN','515.124.4469','FI_ACCOUNT',7800.00,NULL,108,100,'2000-09-09 00:00:00'),(113,'Luis','Popp','LPOPP','515.124.4567','FI_ACCOUNT',6900.00,NULL,108,100,'2000-09-09 00:00:00'),(114,'Den','Raphaely','DRAPHEAL','515.127.4561','PU_MAN',11000.00,NULL,100,30,'2000-09-09 00:00:00'),(115,'Alexander','Khoo','AKHOO','515.127.4562','PU_CLERK',3100.00,NULL,114,30,'2000-09-09 00:00:00'),(116,'Shelli','Baida','SBAIDA','515.127.4563','PU_CLERK',2900.00,NULL,114,30,'2000-09-09 00:00:00'),(117,'Sigal','Tobias','STOBIAS','515.127.4564','PU_CLERK',2800.00,NULL,114,30,'2000-09-09 00:00:00'),(118,'Guy','Himuro','GHIMURO','515.127.4565','PU_CLERK',2600.00,NULL,114,30,'2000-09-09 00:00:00'),(119,'Karen','Colmenares','KCOLMENA','515.127.4566','PU_CLERK',2500.00,NULL,114,30,'2000-09-09 00:00:00'),(120,'Matthew','Weiss','MWEISS','650.123.1234','ST_MAN',8000.00,NULL,100,50,'2004-02-06 00:00:00'),(121,'Adam','Fripp','AFRIPP','650.123.2234','ST_MAN',8200.00,NULL,100,50,'2004-02-06 00:00:00'),(122,'Payam','Kaufling','PKAUFLIN','650.123.3234','ST_MAN',7900.00,NULL,100,50,'2004-02-06 00:00:00'),(123,'Shanta','Vollman','SVOLLMAN','650.123.4234','ST_MAN',6500.00,NULL,100,50,'2004-02-06 00:00:00'),(124,'Kevin','Mourgos','KMOURGOS','650.123.5234','ST_MAN',5800.00,NULL,100,50,'2004-02-06 00:00:00'),(125,'Julia','Nayer','JNAYER','650.124.1214','ST_CLERK',3200.00,NULL,120,50,'2004-02-06 00:00:00'),(126,'Irene','Mikkilineni','IMIKKILI','650.124.1224','ST_CLERK',2700.00,NULL,120,50,'2004-02-06 00:00:00'),(127,'James','Landry','JLANDRY','650.124.1334','ST_CLERK',2400.00,NULL,120,50,'2004-02-06 00:00:00'),(128,'Steven','Markle','SMARKLE','650.124.1434','ST_CLERK',2200.00,NULL,120,50,'2004-02-06 00:00:00'),(129,'Laura','Bissot','LBISSOT','650.124.5234','ST_CLERK',3300.00,NULL,121,50,'2004-02-06 00:00:00'),(130,'Mozhe','Atkinson','MATKINSO','650.124.6234','ST_CLERK',2800.00,NULL,121,50,'2004-02-06 00:00:00'),(131,'James','Marlow','JAMRLOW','650.124.7234','ST_CLERK',2500.00,NULL,121,50,'2004-02-06 00:00:00'),(132,'TJ','Olson','TJOLSON','650.124.8234','ST_CLERK',2100.00,NULL,121,50,'2004-02-06 00:00:00'),(133,'Jason','Mallin','JMALLIN','650.127.1934','ST_CLERK',3300.00,NULL,122,50,'2004-02-06 00:00:00'),(134,'Michael','Rogers','MROGERS','650.127.1834','ST_CLERK',2900.00,NULL,122,50,'2002-12-23 00:00:00'),(135,'Ki','Gee','KGEE','650.127.1734','ST_CLERK',2400.00,NULL,122,50,'2002-12-23 00:00:00'),(136,'Hazel','Philtanker','HPHILTAN','650.127.1634','ST_CLERK',2200.00,NULL,122,50,'2002-12-23 00:00:00'),(137,'Renske','Ladwig','RLADWIG','650.121.1234','ST_CLERK',3600.00,NULL,123,50,'2002-12-23 00:00:00'),(138,'Stephen','Stiles','SSTILES','650.121.2034','ST_CLERK',3200.00,NULL,123,50,'2002-12-23 00:00:00'),(139,'John','Seo','JSEO','650.121.2019','ST_CLERK',2700.00,NULL,123,50,'2002-12-23 00:00:00'),(140,'Joshua','Patel','JPATEL','650.121.1834','ST_CLERK',2500.00,NULL,123,50,'2002-12-23 00:00:00'),(141,'Trenna','Rajs','TRAJS','650.121.8009','ST_CLERK',3500.00,NULL,124,50,'2002-12-23 00:00:00'),(142,'Curtis','Davies','CDAVIES','650.121.2994','ST_CLERK',3100.00,NULL,124,50,'2002-12-23 00:00:00'),(143,'Randall','Matos','RMATOS','650.121.2874','ST_CLERK',2600.00,NULL,124,50,'2002-12-23 00:00:00'),(144,'Peter','Vargas','PVARGAS','650.121.2004','ST_CLERK',2500.00,NULL,124,50,'2002-12-23 00:00:00'),(145,'John','Russell','JRUSSEL','011.44.1344.429268','SA_MAN',14000.00,0.40,100,80,'2002-12-23 00:00:00'),(146,'Karen','Partners','KPARTNER','011.44.1344.467268','SA_MAN',13500.00,0.30,100,80,'2002-12-23 00:00:00'),(147,'Alberto','Errazuriz','AERRAZUR','011.44.1344.429278','SA_MAN',12000.00,0.30,100,80,'2002-12-23 00:00:00'),(148,'Gerald','Cambrault','GCAMBRAU','011.44.1344.619268','SA_MAN',11000.00,0.30,100,80,'2002-12-23 00:00:00'),(149,'Eleni','Zlotkey','EZLOTKEY','011.44.1344.429018','SA_MAN',10500.00,0.20,100,80,'2002-12-23 00:00:00'),(150,'Peter','Tucker','PTUCKER','011.44.1344.129268','SA_REP',10000.00,0.30,145,80,'2014-03-05 00:00:00'),(151,'David','Bernstein','DBERNSTE','011.44.1344.345268','SA_REP',9500.00,0.25,145,80,'2014-03-05 00:00:00'),(152,'Peter','Hall','PHALL','011.44.1344.478968','SA_REP',9000.00,0.25,145,80,'2014-03-05 00:00:00'),(153,'Christopher','Olsen','COLSEN','011.44.1344.498718','SA_REP',8000.00,0.20,145,80,'2014-03-05 00:00:00'),(154,'Nanette','Cambrault','NCAMBRAU','011.44.1344.987668','SA_REP',7500.00,0.20,145,80,'2014-03-05 00:00:00'),(155,'Oliver','Tuvault','OTUVAULT','011.44.1344.486508','SA_REP',7000.00,0.15,145,80,'2014-03-05 00:00:00'),(156,'Janette','K_ing','JKING','011.44.1345.429268','SA_REP',10000.00,0.35,146,80,'2014-03-05 00:00:00'),(157,'Patrick','Sully','PSULLY','011.44.1345.929268','SA_REP',9500.00,0.35,146,80,'2014-03-05 00:00:00'),(158,'Allan','McEwen','AMCEWEN','011.44.1345.829268','SA_REP',9000.00,0.35,146,80,'2014-03-05 00:00:00'),(159,'Lindsey','Smith','LSMITH','011.44.1345.729268','SA_REP',8000.00,0.30,146,80,'2014-03-05 00:00:00'),(160,'Louise','Doran','LDORAN','011.44.1345.629268','SA_REP',7500.00,0.30,146,80,'2014-03-05 00:00:00'),(161,'Sarath','Sewall','SSEWALL','011.44.1345.529268','SA_REP',7000.00,0.25,146,80,'2014-03-05 00:00:00'),(162,'Clara','Vishney','CVISHNEY','011.44.1346.129268','SA_REP',10500.00,0.25,147,80,'2014-03-05 00:00:00'),(163,'Danielle','Greene','DGREENE','011.44.1346.229268','SA_REP',9500.00,0.15,147,80,'2014-03-05 00:00:00'),(164,'Mattea','Marvins','MMARVINS','011.44.1346.329268','SA_REP',7200.00,0.10,147,80,'2014-03-05 00:00:00'),(165,'David','Lee','DLEE','011.44.1346.529268','SA_REP',6800.00,0.10,147,80,'2014-03-05 00:00:00'),(166,'Sundar','Ande','SANDE','011.44.1346.629268','SA_REP',6400.00,0.10,147,80,'2014-03-05 00:00:00'),(167,'Amit','Banda','ABANDA','011.44.1346.729268','SA_REP',6200.00,0.10,147,80,'2014-03-05 00:00:00'),(168,'Lisa','Ozer','LOZER','011.44.1343.929268','SA_REP',11500.00,0.25,148,80,'2014-03-05 00:00:00'),(169,'Harrison','Bloom','HBLOOM','011.44.1343.829268','SA_REP',10000.00,0.20,148,80,'2014-03-05 00:00:00'),(170,'Tayler','Fox','TFOX','011.44.1343.729268','SA_REP',9600.00,0.20,148,80,'2014-03-05 00:00:00'),(171,'William','Smith','WSMITH','011.44.1343.629268','SA_REP',7400.00,0.15,148,80,'2014-03-05 00:00:00'),(172,'Elizabeth','Bates','EBATES','011.44.1343.529268','SA_REP',7300.00,0.15,148,80,'2014-03-05 00:00:00'),(173,'Sundita','Kumar','SKUMAR','011.44.1343.329268','SA_REP',6100.00,0.10,148,80,'2014-03-05 00:00:00'),(174,'Ellen','Abel','EABEL','011.44.1644.429267','SA_REP',11000.00,0.30,149,80,'2014-03-05 00:00:00'),(175,'Alyssa','Hutton','AHUTTON','011.44.1644.429266','SA_REP',8800.00,0.25,149,80,'2014-03-05 00:00:00'),(176,'Jonathon','Taylor','JTAYLOR','011.44.1644.429265','SA_REP',8600.00,0.20,149,80,'2014-03-05 00:00:00'),(177,'Jack','Livingston','JLIVINGS','011.44.1644.429264','SA_REP',8400.00,0.20,149,80,'2014-03-05 00:00:00'),(178,'Kimberely','Grant','KGRANT','011.44.1644.429263','SA_REP',7000.00,0.15,149,NULL,'2014-03-05 00:00:00'),(179,'Charles','Johnson','CJOHNSON','011.44.1644.429262','SA_REP',6200.00,0.10,149,80,'2014-03-05 00:00:00'),(180,'Winston','Taylor','WTAYLOR','650.507.9876','SH_CLERK',3200.00,NULL,120,50,'2014-03-05 00:00:00'),(181,'Jean','Fleaur','JFLEAUR','650.507.9877','SH_CLERK',3100.00,NULL,120,50,'2014-03-05 00:00:00'),(182,'Martha','Sullivan','MSULLIVA','650.507.9878','SH_CLERK',2500.00,NULL,120,50,'2014-03-05 00:00:00'),(183,'Girard','Geoni','GGEONI','650.507.9879','SH_CLERK',2800.00,NULL,120,50,'2014-03-05 00:00:00'),(184,'Nandita','Sarchand','NSARCHAN','650.509.1876','SH_CLERK',4200.00,NULL,121,50,'2014-03-05 00:00:00'),(185,'Alexis','Bull','ABULL','650.509.2876','SH_CLERK',4100.00,NULL,121,50,'2014-03-05 00:00:00'),(186,'Julia','Dellinger','JDELLING','650.509.3876','SH_CLERK',3400.00,NULL,121,50,'2014-03-05 00:00:00'),(187,'Anthony','Cabrio','ACABRIO','650.509.4876','SH_CLERK',3000.00,NULL,121,50,'2014-03-05 00:00:00'),(188,'Kelly','Chung','KCHUNG','650.505.1876','SH_CLERK',3800.00,NULL,122,50,'2014-03-05 00:00:00'),(189,'Jennifer','Dilly','JDILLY','650.505.2876','SH_CLERK',3600.00,NULL,122,50,'2014-03-05 00:00:00'),(190,'Timothy','Gates','TGATES','650.505.3876','SH_CLERK',2900.00,NULL,122,50,'2014-03-05 00:00:00'),(191,'Randall','Perkins','RPERKINS','650.505.4876','SH_CLERK',2500.00,NULL,122,50,'2014-03-05 00:00:00'),(192,'Sarah','Bell','SBELL','650.501.1876','SH_CLERK',4000.00,NULL,123,50,'2014-03-05 00:00:00'),(193,'Britney','Everett','BEVERETT','650.501.2876','SH_CLERK',3900.00,NULL,123,50,'2014-03-05 00:00:00'),(194,'Samuel','McCain','SMCCAIN','650.501.3876','SH_CLERK',3200.00,NULL,123,50,'2014-03-05 00:00:00'),(195,'Vance','Jones','VJONES','650.501.4876','SH_CLERK',2800.00,NULL,123,50,'2014-03-05 00:00:00'),(196,'Alana','Walsh','AWALSH','650.507.9811','SH_CLERK',3100.00,NULL,124,50,'2014-03-05 00:00:00'),(197,'Kevin','Feeney','KFEENEY','650.507.9822','SH_CLERK',3000.00,NULL,124,50,'2014-03-05 00:00:00'),(198,'Donald','OConnell','DOCONNEL','650.507.9833','SH_CLERK',2600.00,NULL,124,50,'2014-03-05 00:00:00'),(199,'Douglas','Grant','DGRANT','650.507.9844','SH_CLERK',2600.00,NULL,124,50,'2014-03-05 00:00:00'),(200,'Jennifer','Whalen','JWHALEN','515.123.4444','AD_ASST',4400.00,NULL,101,10,'2016-03-03 00:00:00'),(201,'Michael','Hartstein','MHARTSTE','515.123.5555','MK_MAN',13000.00,NULL,100,20,'2016-03-03 00:00:00'),(202,'Pat','Fay','PFAY','603.123.6666','MK_REP',6000.00,NULL,201,20,'2016-03-03 00:00:00'),(203,'Susan','Mavris','SMAVRIS','515.123.7777','HR_REP',6500.00,NULL,101,40,'2016-03-03 00:00:00'),(204,'Hermann','Baer','HBAER','515.123.8888','PR_REP',10000.00,NULL,101,70,'2016-03-03 00:00:00'),(205,'Shelley','Higgins','SHIGGINS','515.123.8080','AC_MGR',12000.00,NULL,101,110,'2016-03-03 00:00:00'),(206,'William','Gietz','WGIETZ','515.123.8181','AC_ACCOUNT',8300.00,NULL,205,110,'2016-03-03 00:00:00');
   
   
   #员工部门表
   CREATE TABLE `departments` (
     `department_id` int(4) NOT NULL AUTO_INCREMENT,#部门编号
     `department_name` varchar(3) DEFAULT NULL,#部门名称
     `manager_id` int(6) DEFAULT NULL,#部门领导的员工编号
     `location_id` int(4) DEFAULT NULL,#位置编号
     PRIMARY KEY (`department_id`),
     KEY `loc_id_fk` (`location_id`),
     CONSTRAINT `loc_id_fk` FOREIGN KEY (`location_id`) REFERENCES `locations` (`location_id`)
   ) ENGINE=InnoDB AUTO_INCREMENT=271 DEFAULT CHARSET=utf8;
   
   insert  into `departments`(`department_id`,`department_name`,`manager_id`,`location_id`) values (10,'Adm',200,1700),(20,'Mar',201,1800),(30,'Pur',114,1700),(40,'Hum',203,2400),(50,'Shi',121,1500),(60,'IT',103,1400),(70,'Pub',204,2700),(80,'Sal',145,2500),(90,'Exe',100,1700),(100,'Fin',108,1700),(110,'Acc',205,1700),(120,'Tre',NULL,1700),(130,'Cor',NULL,1700),(140,'Con',NULL,1700),(150,'Sha',NULL,1700),(160,'Ben',NULL,1700),(170,'Man',NULL,1700),(180,'Con',NULL,1700),(190,'Con',NULL,1700),(200,'Ope',NULL,1700),(210,'IT ',NULL,1700),(220,'NOC',NULL,1700),(230,'IT ',NULL,1700),(240,'Gov',NULL,1700),(250,'Ret',NULL,1700),(260,'Rec',NULL,1700),(270,'Pay',NULL,1700);
   (```)
   ```

#### DQL语言的学习

 - 基础查询
 - 语法:select  查询列表  from 表名  查询列表可以是：表中的字段，常量，表达式，函数等等。
 - 特点：查询的结果是一个虚拟的表格，不是真实存在的。

##### 查询表中的单个字段

- select last_name from employee;

##### 查询表中多个字段

- select first_name,last_name from employee;

##### 查询表中的所有的字段

- select * from employee;

##### 查询常量值

- select 100; 后面不需要加上from
- select 'jone' 后面不需要加上from 

##### 查询表达式

 - select 100*90 ;

##### 查询函数

- select version(); 可以用来查看mysql 的版本号。

##### 起别名

- 好处：
  - 便于理解
  - 如果要查询的字段有重名的情况，使用别名可以区分开来
- 方式一：使用as 关键字
  - select last_name as 姓, first_name as 名 from employee;
- 方式二：使用空格
  - select last_name 姓 ,first_name 名 from employee;
- 方式三：使用“. ”双引号起别名
  - select last_name as "第一个 姓" from employee;

##### 去重(distinct)关键字

 - 案例 查询员工表中涉及到的所有的部门编号
    - sselect   distinct e .department_id from employees e;

##### MySQL中+号的作用

 - 在mysql中+ 只有一个功能，运算符

 - 在mysql中，两个操作数都为数值型，则做加法运算

    - select 100+90;

- 如果一方为字符型，mysql会试图将字符型转换数值型，如果转换成功的话，则继续做加法运算，转换不成的话，则该字段被当作0操作。

  - select '123'+90;结果是213
  - select 'john'+90;结果是90

- 在mysql中只有其中一个字段是null，则结果一定是null；

  - select null+'90' 结果是null；

- 字段连接(concat())函数 

  - 在mysql中使用concat()函数连接字段

    - ```sql
      select concat(first_name,last_name) as 姓名 from employees;
      ```

- ifnull(expr1,expr2) 当expr1字段为null时，显示为expr2

  - ```sql
    #当commission_pct为null时，则显示为0 ,不为null时则显示对应的字段值
    select ifnull(commission_pct,0) ,commission_pct 奖金率 from employees;
    ```

#### 条件查询

 - 语法：	select * from 表名 where 筛选条件

 - 分类：

    - 一，按条件表达式筛选 条件表达式。> 大于 < 小于 = 等于 <>不等于  >= 大于等于 <= 小于等于
    - 按逻表达式筛选 逻辑运算符 and or not
    - 模糊查询 like between....and in is null

- 条件运算符的使用

  - 查询员工工资大于12000的信息

    - ```sql
      select  * from employees where salary>12000
      ```

  - 查询部门编号不等于90的员工 的员工名字和部门编号

    - ```sql
      select first_name,last_name from employees where department_id<>90
      ```

- 按逻辑表达式筛选

  - 案例：查询员工的工资在1万和2万之间的员工的名字，工资，以及奖金

    - ```sql
      select concat(first_name,last_name) 姓名, salary 工资 , ifnull(commission_pct,0) 奖金 from employees where salary>=10000 and salary<=20000;
      ```

  - 案例二：查询部门编号不是在90到100之间，或者工资高于15000的员工的信息

    - ```sql
      select * from employees where department_id <90 or department_id>100 or salary>15000;
      ```

- 模糊查询 like. Between .. and. in is null is not null

  - 案例一： 查询员工名字中包含字符a的员工的信息

    ```sql
    select last_name from employees where last_name like '%a%';
    ```

  - like特点：

    - 1⃣️：一般和通配符搭配使用
    - 通配符: % 表示任意多个字符,包含0个字符
    - _ 任意单个字符

    - 案例一：查询员工名字中第三个字符是n，第五个字符是l的员工姓名和工资。

      - ```sql
        select last_name,salary from employees where last_name like '__n_l%';
        ```

    - 案例二:查询员工名字中第二个字符是_的员工的名字和工资。

      - ```sql
        #方法一：可以直接使用转义字符
        select last_name,salary from employees where last_name like '_\_%';
        #方法二： 其中$表示转义的意思 escape 表示需要转义的字符表示 推荐使用
        select  last_name,salary from employees where last_name like '_$_%' escape '$';
        ```

  - betwween ……. and 表示在什么什么之间

    - 案例一：查询员工编号在100和200之间的员工信息

      ```sql
      select * from employees where employee_id between 100 and 200
      ```

  - in 判断某个字段的值，是否属于in列表中的某一项

    - 特点：

      - 使用in提高语句的简洁度
      - in列表的值的类型必须是一致的或者兼容
      - in是不支持通配符和百分号%的。

    - 案例一：查询员工的工种编号是AD_PRES，IT_PROG，AD_VP的员工信息

      - ```sql
        select * from  employees where job_id in('AD_PRES','IT_PROG','AD_VP');
        ```

  - is null  或者is not null 判断该字段的是null 或者不是null

    - 案例一:查询员工表中没有奖金的员工信息

      - ```sql
        select * from employees where commission_pct is null ;
        ```

    - 案例二：查询员工表中有奖金的员工信息

      - ```sql
        select * from employees where commission_pct is not null ;
        ```

    - 安全等于<=>:表示等于某个值

      - 案例一：查询员工表中没有奖金的员工信息

      - ```sql
        select * from employees where commission_pct <=> null ;
        ```

      - 案例二：查询员工表中员工工资是12000的员工的信息

        - ```sql
          select salary from employees  where salary <=>12000;
          ```

  - 经典面试题：

    - ```sql
      select * from employee;
      select * from employee where commission_pct like '%%' and last_name like'%%';
      
      上面的两个sql查询的结果又啥区别
      答案：
      	如果commission_pct和last_name 该字段的值为null的第二条sql的结果会过滤掉为null的人员信息。
      ```

  - 排序查询 (order by)

    - 特点：

      - 1.asc 代表的是升序,desc 代表的是降序 如果不写默认是升序
      - 2.order by 子句中可以支持单个字段，多个字段，表达式，函数， 别名
      - 3.order by 子句一般是放在查询的语句中的最后面，limit除外。

    - 语法：select * from employee [where 筛选条件] order by 排序列表 [asc|desc]

      - 案例一：查询员工信息，要求工资从高到低排序

        - ```sql
          #从高到低
          select * from employees order by salary desc;
          #从低到高
          select * from employees order by salary asc;
          ```

      - 案例二：查询部门编号>=90的员工信息，按入职时间的先后进行排序

        - ```sql
          select * from employees where department_id>=90 order by  hiredate asc;
          ```

      - 案例三：按年薪的高低显示部门员工的信息和年薪，【按表达式排序】

      - ```sql
        #按照别名排序
        select salary, salary*12*(1+(ifnull(commission_pct,0))) 年薪 from employees order by 年薪;
        ```

        ```sql
        #按照表达式排序
        select salary, salary*12*(1+(ifnull(commission_pct,0))) 年薪 from employees order by salary*12*(1+(ifnull(commission_pct,0)));
        ```

      - 案例四：按姓名的长度显示员工的姓名和工资【按函数排序】

        - ```sql
          #按照函数排序
          select length(last_name) ,last_name,salary from employees order by length(last_name);
          ```

      - 案例五：查询员工信息，要求按工资排序，再按员工编号排序

        - ```sql
          #多个字段排序，
          select * from employees order by salary desc ,employee_id asc;
          ```

  - 常见函数：

    - 概念：类似于java中的方法，将一组逻辑语句封装在方法中，对外暴露方法名字
      - 好处：
        - 1.隐藏了实现的细节，2.提高了代码的重用性
      - 调用：
        - select 函数名(参数) from 表名
      - 特点：
        - 函数名
        - 函数的功能
      - 分类
        - 1.单行函数
          - 如 concat(str1,str2,str3) 链接字符，length(str) 字段长度，ifnull()
        - 分组函数
          - 功能：做统计使用，又被称为统计函数，聚合函数，组函数等等。

  - 字符函数：

    - 1.length 获取参数值的字节个数

      - ```sql
        select length('john') ;
        select length(last_name) from employees;
        ```

    - 2.concat(str1,str2)连接字符串

      - ```sql
        select concat(last_name,'_','first_name') from employee;
        ```

    - 3.upper转大写,lower转小写

      -  `````sql
         #转大写
         select upper('john');
         #转小写
         select lower('JOHN');
         `````

    - 案例一：将姓变成大写，名字变成小写，然后拼接在一起。

      - `````sql
        select concat(upper(last_name),'_',lower(first_name)) 姓名 from employees;
        `````

    - 4.substr()msubstring()字符串截取：

      - ```sql
        #在sql中索引是从1开始的 第一个参数表示从字符串，第二个参数表示从指定的索引处开始截取，一直到结束
        select substr('李莫愁爱上了陆展元',7) ;
        #表示从指定的指定的索引处开始截取，截取指定的长度；
        select substr('李莫愁爱上了陆展元',1,3)
        ```

    - 案例二：姓名中首字符大写，其他字符小写然后使用+拼接，显示出来

      - ```sql
        select concat(upper(substr(last_name,1,1)),'_',lower(substr(last_name,2))) from employees;
        ```

    - 5.instr：返回子串第一次出现的索引，如果找不到返回的是0

      - ```sql
        #返回殷六侠第一次出现的索引，如果找不到的话则返回的是0
        select instr('杨不悔爱上了殷六侠','殷六侠') 索引;
        ```

    - trim()：去除前后的空格

      - ```sql
        #	去除前后左右的空格
        select length(trim('       kkkk      '));
        #去除前后指定的字符串，from后面的字符串可以完全去除掉
        select trim('a'from 'aaaaaa张aaaaa翠山aaaaaaaa');
        ```

    - lpad()：用指定的字符实现左填充

      - ```sql
        #不足10的用0补全10位 结果类似于0000000012
        select lpad('12',10,'0');
        ```

    - rpad():使用指定的字符实现右填充

      - ````sql
        #不足10的使用0补全10位结果类似于1200000000
        select rpad('12',10,'0');
        ````

    - replace()：实现字符的替换

      - ```sql
        #实现字符的替换，周芷若被替换成了赵敏
        select replace('张无忌爱上了周芷若','周芷若','赵敏') ;
        ```

  - 数学函数；

    - round 四舍五入

      ````sql
      #四舍五入
      select round(1.55);
      ````

    - cell 向上取整，返回>=该参数的最小整数

      ````sql
      #向上取整
      select cell(1.2)
      ````

    - floor 向下取整，返回<=该参数的最大整数

      ````sql
      #向上取整
      select floor(-9.99);
      ````

    - truncate :截取小数点后指定的位数

    - ````sql
      #截取小数点后一位
      select truncate(1.89,1);
      ````

    - mod():取余数

      - ```sql
        #mod取模，也被称为取余数
        select mod(10,3) ;
        ```

  - 日期函数：

    - now():返回当前系统日期➕时间

      - ```sql
        select now();
        ```

    - curdate():返回当前是的系统日期，不包含时间

      - ```sql
        select curdate();
        ```

    - curtime():返回当前系统时间，不包含日期

      - ````sql
        select curtime();
        ````

    - 获取指定的部分，年，月，日，小时，分钟，秒

    - ````sql
      #获取当前的系统的年
      select YEAR(now()) 年;
      select YEAR('1998-01-01') 年; 返回的是1998;
      select YEAR(hiredate) from employees;
      	
      #获取当前系统的月
      select MONTH(now()) 月;
      
      ````

    - str_to_date();将字符串通过指定的格式转换为日期。

      ```sql
      select str_to_date('03-04-1998','%c-%d-%Y');
      #查询入职日期在1998年4月3号之后入职的。
      select * from employees where hiredate >=str_to_date('03-04-1998','%c-%d-%Y');
      ```

      对照指定的字段：
      ![](../mysql知识总结/images/chapter02.jpg)

    - date_format:将日期转换成字符

    - ````sql
      select date_format(now(),'%y-%m-%c %H:%h:%i:%s') 日期;
      ````

    - 查询有奖金的员工姓名和入职日期(xx月/xx日/xx年);

      - ```sql
        select concat(first_name,last_name),date_format(hiredate,'%m月%c日%Y年') from employees where commission_pct is not null;
        ```

  - 其他函数：

    - ````sql
      #查看当前mysql版本号
      select version();
      #查看当前正在使用的数据库
      select database();
      #查看当前的用户
      select user();
      ````

  - 流程控制函数

    - if 类似于java的if--else函数

      - ```sql
        #select (条件表达式,'结果1','结果2');条件表达式成立的话，执行1，否则执行2
        select if(10>5,'大','小') 结果;
        ```

    - 查询有奖金的员工的姓名和奖金，要是有奖金的话显示嘻嘻，没有奖金的话显示呵呵

      - ````sql
        select last_name,salary,commission_pct, if(commission_pct is null ,'没有奖金,呵呵','又奖金，嘻嘻')from employees;
        ````

    - case函数在mysql中

      - 语法:
      - case 要判断的字段或者表达式 
        - when 常量1 then 要显示的值1或者语句1
        - when 常量2 then 要显示的值2或者语句2
        - when 常量3 then 要现实的值3货真语句3

    - 案例一：#给员工涨工资，部门为30的涨工资1.1倍 部门为40的涨工资1.2倍，部门为50的涨工资1.3倍 其他的部不涨工资

      ```sql
      #case方式的使用的第一种情况
      select department_id,salary 原始工资,
             case department_id
                 when 30 then salary*1.1
                 when 40 then salary*1.2
                 when 50 then salary*1.3
                 else salary
             end 涨幅之后的工资
      from employees;
      ```

    - 语法二：

      - case
      - when 常量1 then 要显示的值或者语句1
      - when 常量2 then 要显示的值或者语句2
      - when 常量3 then 要显示的值或者语句3
      - else 
      - end

    - ```sql
      case的第二种用法
      select last_name,salary 原始工资,department_id,
             case
                 when department_id=30 then salary*1.1
                 when department_id=40 then salary*1.2
                 when department_id=50 then salary*1.3
                 else salary
            end 涨幅之后的工资
      from employees order by department_id
      ```

    - 案列二：

      - 显示部门员工的工资情况，大于20000的为A，大于15000的为B，大于10000的为C，大于5000为D，其他的为E

        - ```sql
          select salary,last_name,
                 case
                     when salary>20000 then 'A'
                     when salary>15000 then 'B'
                     when salary>10000 then 'c'
                     when salary>5000 then 'd'
                     else 'e'
                     END 工资水平
          from employees
          ```

  - 分组函数:

    - 功能:用于统计使用，又称为聚合函数或者统计函数，或者组函数

    - 分类：

      - sum()求和，avg()平均值，max()最大值，min()最小值，count()求和

    - 1.sum()简单使用

    - ```sql
      #查询工资的总和
      select sum(salary) from employee;
      #查询平均工资
      select avg(salary) from employee;
      #查询最大的工资
      select max(salary) from employee;
      #查询最小的工资
      select min(salary) from employee;
      #查询发工资的人的个数
      select count(salary) from employee;
      #聚合函数一块使用
      select sum(salary),avg(salary),count(salary),max(salary),min(salary) from employees
      ```

    - 特点：

      - 1.sum(),avg() 一般被用于处理数值型

      - 2.max(),min(),count() 可以被用于处理任何类型的数据。

      - 3.sum()和avg(),max(),min(),count()是忽略null值的.

      - 4.可以搭配distinct 去除重复的数据

      - ````sql
        select sum(salary),avg(salary),count(salary),max(salary),min(salary) from employee
        ````

      - count()函数的详细介绍

        - coutn(字段名字) 统计该字段不为空的情况下有多少列。
        - count(*)表示统计该表中有多少列，
        - count(1)表示统计该表中有多少列，其中1可以用任意的常量代替。
        - 效率：
          - MYISAM存储引擎下面，count(*)的效率是最高的
          - INNODB存储引擎下面，count(*)和count(1)的效率差不多的，比count(字段)要高一些,因为count(字段)的话，会判断该字段是否为空。

      - 和分组函数一同查询的字段有限制的

        - ```sql
          #和分组函数一起查询的字段一般是group by 后面的字段
          select avg(salary)  from employees;
          ```

        - 案例三：查询员工表中最大入职时间和最小入职时间的相差的天数

          ```sql
          #datediff 用于计算两个日期相差的天数
          select datediff(max(hiredate),min(hiredate)) 天数,max(hiredate),min(hiredate) from employees;
          ```

    - group by 的用法：

      - 语法：

        - select 分组函数，列(要求出现在group by的后面)
        - from 表名 [where 筛选条件] group by 分组列表 [order by 子句]；
        - 注意：
          - 查询列表表特殊,要求是分组函数和group by后面出现的字段。

      - 案例一：查询每个部门的平均工资

        - ```sql
          select avg(salary) 平均工资,department_id 部门id from employees group by department_id;
          ```

      - 添加筛选条件

        - 案例一：查询邮箱中含有a的字符，每个部门的平均工资

          - ````sql
            select avg(salary),department_id from employees where email like '%a%' group by department_id;
            ````

        - 案例二；查询有奖金的每个领导手下员工的最高工资

          - ```sql
            select max(salary),manager_id from employees where commission_pct is not null group by manager_id;
            
            ```

      - 添加分组后的筛选条件

        - 案例一：查询每个部门的员工数量大于2

          - ````sql
            案例分析：
            1.先查询出来每个部门的人数，
            	select count(*),department_id from employees group by department_id;
            2.再根据每个部门的人数，筛选出来人数大于2的部门的信息
            	select count(*) 人数,department_id from employees group by department_id having 人数>2;
            	
            添加分组后的筛选条件，使用having过滤该条件，having 必须放在group by的后面。where 必须放在group by的前面。
            ````

        - 案例二：查询每个工种有工资的员工的最高工资

          - ````sql
            select max(salary) 最高工资,job_id from employees where commission_pct is not null  group by job_id having 最高工资>12000;
            ````

        - 案例三：查询领导编号大于120，并且每个领导的员工的最低工资大于5000的领导是那个，以及最低工资

          - ```sql
            select min(salary) 最低工资,manager_id from employees where manager_id >120 group by manager_id having 最低工资>5000;
            
            ```

        - 特点：

          |            |        位置         | 关键字 | 数据源         |
          | ---------- | :-----------------: | -----: | -------------- |
          | 分组前筛选 | group by子句的前面  |  where | 原始表         |
          | 分组后筛选 | group by 子句的后面 | having | 分组后的结果集 |

          - 注意：
            - 分组函数做条件肯定是放在having子句中。
            - 能用分组前筛选的话，优先分组前筛选。
          - group by子句支持单个字段分组，多个字段分组(多个字段之间用逗号隔开,没有顺序要求),表达式或者函数。
          - 可以和排序一块使用，但是放在最后的。


  - 按分组函数或者 表达式分组

    - 案例一：按员工姓名的长度分组，查询每一组的员工个数，筛选员工个数>5的有哪一些

      - ```sql
        #按照表达式分组 count(*)分组
        select length(first_name) 长度  ,count(*) from employees group by length(first_name) having count(*)>5;
        ```

  - 按多个字段分组

    - 案例一:查询每个部门每个工种的员工的平均工资。

      - ````sql
        select avg(salary) from employees group by job_id,department_id;
        ````

    - 添加排序：

      - ```sql
        #使用order by 排序
        select avg(salary)  平均工资 from employees group by job_id,department_id order by 平均工资 desc;
        ```

      - 案例三：查询最高工资和最低工资的差距

      - ```sql
        select (max(salary)-min(salary)) from employees;
        ```

  - 连接查询

    - 含义：又称多表查询，当查询的字段来自于多个表时，就会用到连接查询

    - 案例一：查询表中对应的男女朋友的关系

      - ````sql
        select y.name,s.boyName from beauty y,boys s
        where y.boyfriend_id = s.id;
        ````

    - 分类：

      - 按年代分类：
        ​	sql92标准  sql99标准

      - 按功能分类：

        - 内链接:

          - 等值连接:

          - 特点：多表等值连接的结果为多表的交集部分。

          - n表连接，至少需要n-1个链接条件

          - 多表连接的顺序没有要求

          - 一般需要为表起别名

          - 可以搭配前面介绍的所有子句使用，比如排序，分组和筛选。

            - ```sql
              #等值连接，boyfriend = id 的时候会匹配出来
              #查询女神名和对应的男神名字
              select y.name,s.boyName from beauty y,boys s
              where y.boyfriend_id = s.id;
              ```

            - 案例二：查询员工名和对应的部门名字

            - ```sql
              #取值具有相同意义的字段的id
              select e.last_name,d.department_name  from employees e,departments d
              where e.department_id = d.department_id;
              ```

            - 案例三:

              ```sql
              #查询员工名，工种号，工种名字
              select e.last_name,d.department_name  from employees e,departments d
              where e.department_id = d.department_id;
              ```

            - 案例四：添加筛选条件使用and连接

              - ```sql
                select e.last_name,j.job_title from employees e ,jobs j
                where e.job_id  = j.job_id
                and e.commission_pct is not null;
                ```

              - 案例五：查询城市名中第二个字符为o的部门名称和城市名字

              - ````sql
                select l.city,d.department_name from locations l,departments d
                where l.location_id = d.location_id
                and d.department_name like '_o%'
                ````

            - 添加分组函数

              - 查询每个城市的部门个数

                - ````sql
                  select count(*),l.city from departments d,locations l
                  where d.location_id = l.location_id
                  group by l.city;
                  ````

                - 查询又奖金的每个部门的部门名称和部门的领导编号和该部门的最低工资

                  - ````sql
                    select d.department_name,d.manager_id,min(salary) from departments d,employees e
                    where d.manager_id = e.manager_id and e.commission_pct is not null
                    group by d.manager_id,d.department_name;
                    ````

                - 查询每个工种的工种名称和员工的个数，并且按照员工跟书降序排列

                - ````sql
                  #先分组在排序
                  select j.job_title,count(*) 个数 from employees e,jobs j
                  where e.job_id = j.job_id
                  group by j.job_title
                  order by 个数;
                  ````

                - ```sql
                  #三表连接,使用and连接
                  select e.last_name,d.department_name,l.city from employees e,departments d,locations l
                  where e.department_id = d.department_id
                  and d.location_id = l.location_id
                  and l.city like 'S%';
                  ```

                - 

          - 非等值连接

            - 测试非等职连接：

              ```sql
              CREATE TABLE job_grades
              (grade_level VARCHAR(3),
               lowest_sal  int,
               highest_sal int);
              
              INSERT INTO job_grades
              VALUES ('A', 1000, 2999);
              
              INSERT INTO job_grades
              VALUES ('B', 3000, 5999);
              
              INSERT INTO job_grades
              VALUES('C', 6000, 9999);
              
              INSERT INTO job_grades
              VALUES('D', 10000, 14999);
              
              INSERT INTO job_grades
              VALUES('E', 15000, 24999);
              
              INSERT INTO job_grades
              VALUES('F', 25000, 40000);
              ```

            - 案例一：查询员工工资和工资等级

            - ```sql
              #在员工表和工资等级表；两个表并没有很多的关联，我们可以使用非等值连接 建立两个表之间的关系。
              select e.salary,j.grade_level
              from employees e,job_grades j
              where e.salary
                        between j.lowest_sal and j.highest_sal;
              ```

            - 

          - 自连接:数据来自同一张表，在连接的时候需要使用该表中的字段对应其他字段

          - ````sql
            #查询员工的姓名和编号以及该员工的领导的名字和编号 
            #第一个表可以看作是员工表，第二个表可以看作领导表
            select e.last_name 员工的名字,e.employee_id 员工id ,
                   m.last_name 该员工对应的领导的名字 ,m.employee_id
            from employees e ,employees m
            where e.manager_id = m.employee_id
            order by  该员工对应的领导的名字 desc ;
            ````

        - Sql99语法：

          - 语法：
          - select 查询列表 from 表一 别名 [连接类型] join on 连接条件 
          - 【where 筛选条件】
          - 【group by 分组】
          - 【having 过滤条件】
          - 【order by 排序】

        - 内链接 inner：

          - 语法：

            - select 查询列表 from 表1 别名 inner join 表2 别名 on 连接条件

            - 分类

              - 等值连接：

              - 案例一：查询员工号和部门号

              - ```sql
                select e.last_name,d.department_name from employees e inner join departments d on e.department_id = d.department_id;
                
                ```

              - 案例二：查询员工名字中包含e的员工的名字和工种号

              - ````sql
                select e.last_name,j.job_title from employees e inner join jobs j on e.job_id = j.job_id
                where e.last_name like '%e%';
                ````

              - 案例三：查询部门个数大于3的城市名和部门个数(分组➕筛选)

              - ````sql
                select count(*) 部门个数,l.city from locations l inner join departments d on l.location_id = d.location_id
                group by l.city having 部门个数>3;
                ````

              - 案例四：查询哪个部门的员工的个数大于3的部门员工和员工个数，并且按个数降序排列

                - ```sql
                  select count(*),d.department_name from employees e
                                                           left join departments d on e.department_id = d.department_id
                  group by d.department_name
                  having count(*)>3 order by count(*) desc
                  ```

              - 案例五：查询员工名字，部门名字，工种名字，并按照部门名称排序

              - ```sql
                select e.last_name,d.department_name,j.job_title from employees e inner join departments d on e.department_id = d.department_id
                inner join jobs j on e.job_id = j.job_id order by d.department_name desc
                ```

              - 非等值连接：

              - 案例一：查询员工的工资级别

              - ```sql
                select e.salary,g.grade_level from employees e inner join  job_grades g on e.salary between g.lowest_sal and g.highest_sal;
                
                ```

              - 案例二: 查询工资级别的个数>2的个数，并且按照工资级别降序排列

              - ````sql
                select g.grade_level,count(*) from employees e inner join job_grades g on e.salary between g.lowest_sal and g.highest_sal
                group by g.grade_level having count(*)>2 order by g.grade_level desc;
                ````

              - 自连接：

              - 案例三：查询姓名中包含字符k的员工的姓名，上级的名字

              - ```sql
                select e.last_name,m.last_name from employees e inner join employees m on e.manager_id = m.employee_id
                where e.last_name like '%k%'
                ```

              - 

        - 外链接

          - 应用场景:

            - 用于查询一个表中有，而另外一个表中没有的记录

          - 特点：

            - 1.外连接的查询结果为主表中的所有的记录
            - 2.如果从表中有和他匹配的，则显示匹配的值。
            - 如果从表中没有和他匹配的则显示null；
              - 外连接查询结果==内链接结果+主表中有而从表中没有的记录。

          - 左外连接：left join 左边的是主表

          - ```sql
            案例一：查询男朋友不在男神表的女神名
            select a.name from beauty a left join boys b on a.boyfriend_id = b.id where b.id is null;
            ```

          - 右外连接：right join 右边的主表

            - ```sql
              #查询男朋友不在男神表的女神名
              select ab.name from boys  b right join beauty ab on b.id = ab.boyfriend_id where b.id is null;
              ```

            - 案例一：查询哪个部门没有员工

            - ```sql
              #左外连接
              select d.department_name ,e.employee_id from departments d left join employees e on d.department_id = e.department_id
              where e.employee_id is null;	
              #右外连接
              select d.department_name,e.employee_id from employees  e right join departments d on e.department_id = d.department_id
              where e.employee_id is null;
              ```

            - 

          - 左外连接和右外连接交换两个表的顺序，可以实现同样的效果。

          - 全外连接：相当于内链接的结果+表1中有但表2中没有的+表2中有但是表1中没有的

        - 交叉连接：cross

        - ```sql
          #实现一个笛卡尔成绩
          select * from boys cross join beauty;
          ```

  - 子查询:

    - 含义：出现在其他语句中的select语句，称为子查询或内查询，外部的查询语句，称为主查询或者外查询。

    - 分类：

      - 按子查询出现的位置：select 后面(仅仅支持标量子查询)，from 后面(表子查询)，where或者having后面(标量子查询,列子查询,行子查询),exists后面(表子查询)

    - 按照结果集的行列数不同：

      - 标量子查询(结果集只有一行一列)
      - 列子查询(结果集只有一列多行)
      - 行子查询(结果集有一行多列)
      - 表子查询(结果集一般是多行多列)

    - 一：where或者having后面的(标量子查询，列子查询,行子查询)

      - 特点：
        + 1.子查询放在小括号内
        + 2.子查询一般放在条件的右侧
        + 3.标量子查询，一般搭配着单行操作符使用 >  < >= <= <>
        + 4.子查询执行是优先于主查询进行的。
      - 列子查询：一般搭配着多行操作符使用 in any/some all

    - 1.标量子查询

    - 案例一：查询谁的工资比Abel的高

      - ```sql
        select last_name,salary from employees where salary>(select salary from employees where  last_name='ABel');
        ```

    - 案例二:查询jod_id 和141号员工相同，salary比143号员工多的，员工的姓名和job_id和工资。

      ```sql
      select last_name,salary,job_id  from employees where job_id =(select job_id from employees where employee_id = 141)and salary>(select salary from employees where employee_id = 143 )
      ```

    - 案例三:查询工资最少的员工的姓名和job_id和工资

      - ````sql
        select last_name,salary,job_id from employees where salary = (select min(salary) from employees);
        ````

    - 案例四：查询最低工资大于50号部门最低工资的部门id和其最低工资。

      - ```sql
        select min(salary),department_id from employees group by department_id
        having min(salary)>(select min(salary) from employees where department_id =50);
        ```

    - 非法使用的标量子查询(子查询返回的结果不是一行一列)

  - 列子查询(多行子查询)的使用，使用多行比较操作符号

    | 操作符     | 含义                       |
    | ---------- | -------------------------- |
    | in/ not in | 等于列表中                 |
    | ANY/some   | 和子查询返回的某一个值比较 |
    | ALL        | 和子查询返回的所有的值比较 |
    |            |                            |

    - 案例一：查询location_id是1400或者1700的所有的员工姓名

      - ```sql
        select last_name from employess where department_id in(
        select department_id from location_id in(1400,1700));
        ```

    - 案例二：查询其他工种中比job_id为"IT_PROG"任意工资低的员工的员工号，姓名和job_id以及salary。

      - ```sql
        select employee_id,last_name,job_id ,salary from employees where salary<any(select salary from employees where job_id='IT_PROG') and job_id<>'IT_PROG';
        ```

    - 案例三：查询其他工种中比job_id为"IT_PROG"所有工资低的员工的员工号，姓名和job_id以及salary。

      - ```sql
        select employee_id,last_name,job_id ,salary from employees where salary<ALL(select salary from employees where job_id='IT_PROG') and job_id<>'IT_PROG';
        ```

  - 行子查询：

    - 案例一：查询出员工编号最小和工资最高的员工的姓名和工资

      - ```sql
        #方式一:
        select last_name,salary from employees where employee_id = (select min(employee_id) from employees) and salary = (select max(salary) from employees);
        #方式二：相当于括号里面的等于括号里面的
        select last_name,salary from employees where (employee_id,salary)  =(select min(employee_id),max(salary) from employees);
        ```

  - select 后面：==比较有意思 可以重点看看== 仅仅只出标量子查询

    - 子查询的结果充当一张表，必须起一个别名

    - 案例一：

      - ```sql
        select d.department_id ,(select count(*) from employees e
                                where d.department_id=e.department_id) 个数
        from departments d
        #下面的sql逻辑是正确的但是结果不是想要的,因为在使用count(*)时会忽略该字段为null的值。
        select count(1),d.department_id from employees e left join departments d on e.department_id = d.department_id
        
        group by d.department_id;
        
        
        ```

    - 案例三：查询每个部门的平均工资等级和平均工资和部门id。

      - ```sql
        select avg_g.平均工资,avg_g.department_id,j.grade_level from (
            select avg(salary) 平均工资 ,department_id from  employees group by department_id
            ) avg_g  inner join  job_grades j on avg_g.平均工资 between j.lowest_sal and j.highest_sal;
        ```

  - exists后面(相关子查询)：

    - exists(完整的查询语句)，返回的结果是1或者0

    - 案例一：查看exists的返回结果

      - ```sql
        select exists(select employee_id from empolyess);返回的结果是1
        select exists(select employee_id from employess where salary =30000)返回的结果是0
        ```

    - 案例二：查询有员工的部门名称

      - ````sql
        #方式一：
        select department_name from departments d where d.department_id in(
            select department_id from employees)
            );
            #方式二
            select department_name from departments d where
            exists(select * from employees e where e.department_id =d.department_id);
        ````

    - 案例二：查询没有难朋友的女神信息

      - ```sql
        select * from beauty  b where not exists(select * from boys ab where ab.id =b.boyfriend_id)
        
        ```

  - 典型案例：

    - 查询各部门工资比本部门平均工资高的员工的员工号，姓名和工资

    - ```sql
      select last_name,salary,e.department_id
      from employees e inner join
               (select avg(salary) 平均工资,department_id from employees  group by department_id) av
      on e.department_id = av.department_id where e.salary>av.平均工资;
      ```

- 分页查询


  - 应用场景：要显示的数据一页显示不了的时候，需要用到分页查询。


    - 关键字   limit   一般放在最后面 ，limit offset, size offset:要显示的条目的起始索引(起始索引从0开始) ，size要显示的条目的个数。

  - 案例一：查询前五条员工信息


    - ```sql
      select * from employees limit 0,5;
      ```

  - 案例二：查询第11条到第25条的记录


    - ````sql
      select * from employees limit 10,15;
      ````

  - 案例三：又奖金的员工信息，并且工资比较高的前10名显示出来。


    - ```sql
      select * from employee where comm_pict is not null order by salary 10 limit 10;
      ```

  - 特点：


    - limit：放在查询语句的最后
    - 索引一般是从0开始
    - 公式： 要显示的页数page，每页的条目size：
    - select 查询列表 from employees limit (page-1)*size ,size;

  - 联合查询：union


    - union联合查询 合并,将多条查询语句的结果合并成一个结果。
    
    - 场景：要查询的结果来自于多个表，且多个表没有直接的连接关系，但要查询的信息一直时
    
    - 特点： 


      - 1.要求多条查询语句的查询列表列数是一致的
      - 2.查询的数据会祛除重复的
      - 3.使用union all 不去除重复的。
    
    -  案例一：


      - ```sql
        select * from employees where last_name like '%a%' or department_id>50;
        #等同于
        select * from employees where last_name like '%a%'
        union
        select * from employees where department_id>50;
        ```

- DML语言：

  - 数据操作语言

    - 插入insert
    - 修改 update
    - 删除 delete

  - 插入语句：

    - 语法：insert into 表名(列名1,列名2,列名3.....)values(值1,值2,值3.....);

    - 插入的值的类型需要与列的类型一致或者兼容。

    - ```sql
      insert into beauty (id,name,sex,borndate,phone,photo,boyfriend_id)
      values (13,'唐艺昕','女','1998-09-09','13858389564',null,'6');
      ```

    - 不可以为null的列必须插入值，可以为null的列如何插入值？

    - ```sql
      #方式一：直接使用null值替代
      insert into beauty (id,name,sex,borndate,phone,photo,boyfriend_id)
      values (13,'唐艺昕','女','1998-09-09','13858389564',null,'6');
      #方式二：字段为空的话，不需要添加该字段。同时省掉字段和值。
      insert into beauty (id,name,sex,borndate,phone,boyfriend_id)
      values (13,'金星','女','1998-09-09','13800000000','9');
      ```

    - 列的顺序可以调换

    - ```sql
      insert  into beauty(name,sex,photo) values ('关晓彤','女','http://www.baidu.com');
      ```

    - 列数必须和字段的值一致。

    - ````sql
      #这是一种错误的方式
      insert  into beauty(name,sex,photo) values ('关晓彤','女','http://www.baidu.com','2019-09-01');
      ````

    - 可以省掉列名，但是字段的值和顺序必须和表中的保持一致。

    - ```sql
      insert into beauty values (13,'唐艺昕','女','1998-09-09','13858389564',null,'6');
      ```

    - 插入的另外一种方式

      - ```sql
        #插入的另外一种方式
        insert into  beauty set id = 16, name ='刘涛', phone ='999' ,boyfriend_id = 9;
        ```

    - 两种方式PK

      - 方式一支持插入多行，方式二不支持

      - 方式一支持自查询，方式二不支持

      - ````sql
        insert into beauty(id,name,phone) select(20,'宋茜','1570000000')
        ````

  - 修改语句：

    - 修改单表中的记录

      - 语法：update 表名 set 列名1 = ‘新值1’,列名2=‘新值2’ where 筛选条件;

      - ```sql
        #修改beauty表中姓唐的女神的电话为138000000
        update beauty set phone ='138000000' where name like '唐%';
        ```

      - 案例二：修改boy表中id号为2的名称为张飞，魅力值10

        - ````sql
          update boy set boyname='张飞' ,usercp='10' where id =2;
          ````

    - 修改多表中的记录。

      - sql92语法：

        ```sql
        update 表1 别名1,表2 别名2 set 列1 = 值1 ，列2=值2 where 连接条件 and 筛选条件
        ```

      - sql99语法：

        - ```sql
          update 表1 别名1 inner|left|right join 表2 别名2 on 连接条件 set 列1=值1，列2=值2 where 筛选条件；
          ```

      - 案例一：修改张无忌的女朋友的电话为113,并且魅力值为200

      - ```sql
        #sql99语法
        update boys b inner join beauty a on b.id =a.boyfriend_id
        set a.phone='1133',b.userCP = 200 where b.boyName='张无忌'
        #sql92语法
        update beauty b ,boys a set b.phone ='124009990' ,a.userCP=70 where b.boyfriend_id = a.id and a.boyName='段誉';
        ```

      - 案例三：修改没有男朋友的女神的男朋友编号为2

        - ```sql
          update beauty b left join boys ab
            on b.boyfriend_id = ab.id set b.boyfriend_id =2 where ab.id is null;
          ```

  - 删除语句：

    - 单表的删除

    - 方式一：delete

      - 语法：delete from 表名 where 筛选条件

        - ```sql
          delete from boys where id = 9；
          ```

        - 

      - truncate table 表名。清空表数据 后面不可以跟where条件

    - 多表的删除

      - 语法：sql92语法：delete 别名1,别名2 from 表1 别名1 ,表2 别名2 where 连接条件 and 筛选条件

      - 语法：sql99：delete 别名1,别名2 from 表1 别名1 inner|left|right join 表2 别名2

      - on 连接条件 where筛选条件

      - 删除段誉的女朋友信息和段誉的信息

      - ````sql
        #sql92
        delete b,ab from boys b ,beauty ab where b.id =ab.boyfriend_id and b.boyName='段誉';
        #sql99
        delete b from boys b left join beauty ab on b.id = ab.boyfriend_id where b.boyName='段誉';
        
        ````

        - | 区别                         | delete                     | truncate   |
          | ---------------------------- | -------------------------- | ---------- |
          |                              | 可以加where条件            | 不能       |
          |                              | 效率较低                   | 效率较高   |
          | 在插入新的数据自动增长的数据 | 从断点处开始               | 从1开始    |
          |                              | 又返回值，返回的是删除几行 | 没有返回值 |
          |                              | 可以回滚                   | 不能回滚   |

- 数据库DDL语言：

  - 主要用来库和表的管理语言。

  - 库的管理：创建，修改和删除

  - 表的管理：创建，修改和删除

  - 创建create 修改：alter 删除drop

    - 库的创建：

    - 语法：create datadase 库名

    - 案例一：创建数据库

    - ```sql
      #方式一
      create database books;
      #方式二：
      create database if not exists books;
      ```

    - 更改数据库字符集：

    - ```sql
      alter database books character set gbk;
      alter database books character set utf8;
      ```

    - 数据库的删除：

    - ```sql
      drop database if exists books; 
      ```

  - 表的管理：

    - 表的创建：

    - 语法：create table 表名(字段名1 类型1(长度) 约束,字段名2 类型2(长度) 约束 );

    - ```sql
       create table book(
        id int ,#编号
        name varchar(20)#姓名
        price double ,#价格
        authorId int ,#作者编号
        publishDate Datetime #出版日期
       );
       ```
      ```
    
    - 表的修改：
    
      - 修改列的类型：
    
        ```sql
        alter table book change column publishDate pushDate Datetime;
      ```

      - 约束修改列名

      - ```sql
        alter table book modify column pushDate TIMEstamp;
        ```

      - 添加新列

        - ```sql
          alter table book add column annual double;
          ```

      - 删除一列

      - ```sql
        alter table book drop column annual;
        ```

      - 修改表名

        - ````sql
          alter table author rename to  book_author
          ````

      - 表的删除：

      - ```sql
        drop table book_author;
        drop table 表名;
        show tables ;#查看当前库的所有的表。
        ```

      - 通常的写法：

        - ```sql
          #创建库
          drop database if exists 旧库名;
          create database 新库名字;
          #创建表
          drop table 表名
          create table 表名();
          
          ```

      - 表的复制：

        - ```sql
          #仅仅复制表的结构
          create table 新表名 like 旧表名
          #复制表中的数据➕表的结构
          create table 新表名 select * from 	旧表名;
          #仅仅复制某一些字段：
          create table 新表名 
          select id,name from 旧表名字 where 1=2;
          
          ```

- Mysql----数据类型

  - 常见的类型：

    - 数值型：

      - 整型：

        - | 字节数 | tinyint | smallint | mediumint | int/Integer | bigInt |
          | ------ | ------- | -------- | --------- | ----------- | ------ |
          |        | 1       | 2        | 3         | 4           | 8      |
          |        |         |          |           |             |        |
          |        |         |          |           |             |        |

        - 特点：在创建的时候默认是有符号的，如果想要设置无符号的话，需要添加unsigend

        - 如果插入的数值超出啦范围，会报错异常，并且是插入的是临界值。

        - 如果不设置长度,会设置默认的长度。长度代表的是显示的最大宽度，如果没有的话，可以在设置的时候使用zerofill代替。

      - 小数型：

        - 定点数：dec(M,D) ，decimal(M,D) 保持的精度是最大的。
          - M和D的含义：D表示小数点后面的位数，M表示最大的位数(整数➕小数)
          - Decimal(M,D):其中M默认是10，D默认是0；
          - float 和double 则会根据插入的数值的精度来决定精度。
        - 浮点数：
          - Float:默认是4个字节
          - Double:默认是8个字节

      - 原则：所选择的类型越简单越好，能保存的数值的类型越小越好。

    - 字符型：

      - 较短的文本：char varchar

      - |         | 写法                       | M的意思        | 特点           | 空间的耗费   | 效率 |
        | ------- | -------------------------- | -------------- | -------------- | ------------ | ---- |
        | char    | char(M),M可以省掉，默认是1 | 最大的字符数   | 固定长度的字符 | 比较耗费空间 | 高   |
        | varchar | varchar(M)不可以省掉，     | 最大的字符数啊 | 可变长度的字符 | 比较节省空间 | 低   |
        |         |                            |                |                |              |      |
        |         |                            |                |                |              |      |

      - 

      - 

      - 较长的文本：text,blob(较长的二进制数据)

    - 日期型：用于保存日期的值，必须使用单引号引起来。

      - date: 4个字节，只有只有日期，
      - datetime:8个字节，有日期和时间,只能反映出插入的当地时区
      - timestamp:4个字节，保存日期和时间和实际的时区有关，更可以反映实际的日期受到mysql和sqlmode的影响很大。
      - time：只有时间。
      - year：只有年

- 经典面试题：

  - delete和truncate	区别：

    - truncate:删除后，如果在插入的话，标示列从1开始。

    - delete:删除后，如果在插入的话，标示列从断点出开始。

    - truncate:不可以添加筛选条件，delete不可以添加筛选条件

    - truncate:效率比较高，delete效率比较低

    - Truncate:没有返回值，delete可以返回受影响的行数。

    - Truncate：删除的数据不可以回滚,delete删除的数据可以回滚。




- 常见的约束：

  - 含义：一种限制，可以限制表中行或者列的数据，为了保证表中数据的准确和可靠性。
  - 分类：六大约束
    - not null 非空约束，用于保证该字段的值不能为空。
    - Default:默认约束，用于保证该字段的值有默认值。
    - Primary key：主键，用于保证该字段的值具有唯一性，并且是非空的。
    - UNIQUE:唯一,用于保证该字段的值具有唯一性，可以为空。
    - CHECK:检查约束[mysql是不支持的]。在oracle和sqlServer中是支持的
    - foreign key：外键，用于限制两个表之间的关系，用于保证该字段的值必须来自于主表的关联列的值，再从表中添加外键约束，用于引用主表中某列的值。

  - 添加约束的时机：

    - 创建表的时候
    - 修改表的时候

  - 约束的分类：

    - 列级约束
      - 六大约束在语法上都支持，但外键约束没有效果
    - 表级约束
      - 除了非空约束，默认，其他的都支持。
    - 注意：主键和外键会默认生成索引。

  - 创建表的时候添加约束：

    ```sql
    create  table students(
       id int primary key ,#主键
       stuName varchar(20) not null ,#非空约束
       gender char(1) check (gender = '男' or gender='女'),#检查约束，在Mysql中不起作用
       seat int unique,# 唯一约束
      age int default 10,#默认约束
      majorId int foreign key  refenerces major(id)#外键
    );
    
    
    create table major(
      id int primary key ,
      majorName varchar(10)
    );
    
    ```

  - 添加表级约束：

    - `````sql
      create table stuInfo(
        id int ,
        stuName varchar(20),
        gender char(1),
        seat int,
        age int ,
        majorId int,
      
        constraint pk primary key (id),#主键
        constraint ck check (gender in('男','女')),#检查约束
        constraint un unique (seat),#唯一约束
        constraint fk_stuInfo_major foreign key (majorId) references major(id)#外键约束
      );
      `````

  - 通用的写法：

    - ```sql
      #sql的通用写法，一般是外键写在最下面，因为一个表中可以有多个外键,其他的约束写在列的后面
      create  table stuInfo(
        id int primary key ,
        stuName varchar(20) not null,
        gender char(1) check(gender = '男' or gender='女'),
        age int default 10,
        set int unique ,
        marjorId int ,
        constraint fk_stuinfo_major foreign key(marjorId) references major(id) 
      );
      ```

  - 主键和唯一的对比：

    - 都可以保证数据唯一性。
    - 主键不可以为空，唯一可以为空。
    - 主键在一个表中，至多只有一个，单数唯一的话在一个表中可以有多个。
    - 都可以组合使用。联合主键或者 联合唯一 ，不推荐使用。

  - 外键的特点：

    - 要求在从表中设外键关系
    - 从表中的外键列的类型和主表中的关联列的类型要求一致，名称无要求
    - 主表中的关联列必须是一个key(一般是主键或者唯一键)
    - 再插入数据时，先插入主表，在插入从表
    - 删除数据时，先删除从表的数据，在删除主表的数据。

  - 修改表的时候删除约束

    - 删除非空约束

    - ```sql
      alter table stuInfo modify column stuName varchar(20) null;
      ```

    - 删除默认约束

    - ````sql
      alter table stuInfo modify  column age int ;
      ````

    - 删除主键

    - ```sql
      alter table stuInfo modify  column id int;
      alter table stuInfo drop primary key;
      ```

    - 删除唯一键

    - ```sql
      alter table stuInfo drop index set;
      ```

    - 删除外键约束

    - ````sql
      alter table stuInfo drop foreign key fk_stuinfo_major
      ````

  - 标示列：

    - 又被称为自增长列，含义可以不用手动的插入值，系统提供默认的序列值。

    - 创建表时 设置标示列

    - ```sql
      create table stu_info(
        id int primary key auto_increment,#设置自增长列
        name varchar(20)
      );
      ```

    - 特点：

      - 标示列必须和主键搭配。
      - 一个表只多有一个标示列(自增长列)
      - 标示列的类型只能是int类型。
      - 标示列可以通过set auto_increment_increment  = 3; 设置步长

    - 在修改表的时候设置标示列

      - ```sql
        alter table stuInfo modify column id int primary key auto_increment;
        ```

    - 在删除表的时候设置标示列

    - ```sql
      alter table stu_info modify id int primary key ;
      ```

- TCL语言(事务控制语言)

  - 事务：事务是由单独的单元的一个或者多个sql语句组成，在这个单元中作为一个不可分割的整体，如果单元中某一条sql语句一旦执行失败或者错误，整个单元将会回滚，所有受到影响的数据将返回事务开始之前的状态，如果单元中的所有的sql语句执行成功，则事物被顺利执行。

  - 储存引擎：

    - 在mysql中中的数据使用不同的技术存储在文件或者(内存)中
    - 通过show engines :来查看mysql支持的存储引擎
    - 在mysql中用的最多的存储引擎有：innodb，myisam，memory等等。其中innodb支持事务，二myisam，memeory等不支持事务。

  - 事务的特点(ACID属性):

    - 原子性：指的是事务是不可分割的工作单位，事务中的操作要么成功,要么都发生，要么都不发生。

    - 一致性：事务必须使数据库从一个一致性状态变换到另外一个一致性状态。

    - 隔离性：是指一个事物的执行不能被其他的事务干扰，即一个事务内部的操作及使用的数据对并发的其他事务是隔离的，并发执行的各个事务之间不能相互干扰。

    - 持久性：指的是一个事务一旦被提交，它对数据库中的数据的改变就是永久性的，接下来的其他操作和数据库故障不应该对其有任何影响。


  - 事务的创建：

    - 显示事务：

      - 事务具有明显的开启和结束的标记，

      - 前提是：必须先设置自动提交功能为禁用。

      - ````sql
        #步骤1：开启事务
        set autocommit  =0;
        start transaction ; #可选的
        #步骤2:便携事务中的sql语句(select,insert,update,delete)等等
        #语句1
        #语句2
        #步骤三：
        #结束事务
        commit #提交事务
        rollback  #回滚事务
        ````

      - 

    - 隐式事务：

      - 事务没有明显的开启和结束的标记。
      - 比如delete，update ，insert等等语句。

    - 隔离级别：

      - 对于同时运行的多个事务，当这一些事务访问数据库中相同的数据时候，如果没有采取必要的隔离机制，就会导致各种并发问题。

      - 脏读：对于两个事务T1，T2，当T1已经读取啦已经被T2更新但是还没有被提交的字段之后，若T2回滚，T1读取的内容就是临时切无效的。

      - 不可重复读：对于两个事务T1,或者T2，T1读取啦一个字段，然后T2更新啦该字段之后，T1再次读取同一个字段，值是不相同的。

      - 幻读：对于两个事务T1,T2,T1从一个表中读取啦一个字段，然后在T2在该表中插入了一些新的行，之后，如果T1再次读取同一个表，就会多出几行。

      - 数据库事务的隔离级别：数据库系统必须具有隔离并发运行各个事务的能力，是他们 不会相互影响，避免各种并发问题。

      - 一个事务与其他事务隔离的程度称之为隔离级别，数据库规定啦多种食物隔离级别，不同隔离级别对应不同的干扰程度，隔离级别越高，数据的一致性就越好，但是并发型越弱。

      - 数据库4中隔离级别：

      - | 隔离级别                     | 描述                                                         |
        | ---------------------------- | ------------------------------------------------------------ |
        | 读未提交（Read Uncommitted） | 允许事务读取没有被其他事务提交的变更，脏读，不可重复读和幻读的问题都会出现 |
        | 读提交（Read Committed       | 只允许事务读取已经被其他事务提交的变更，可以避免脏读，但不可重复读和幻读还存在。 |
        | 可重复读（Repeated Read）    | 确实事务可以多次从一个字段中读取相同的值，在这个事务持续期间，禁止其他事务对这个字段进行更新，可以避免脏读和不可重复读，单数幻读的问题仍然存在 |
        | 串行化（Serializable）       | 确保事务可以从一个表中读取相同的行，在这个事务持续期间，禁止其他事务对该表执行插入，更新和删除等等，所有的并发问题都可以避免，但是性能十分低下。 |
        |                              |                                                              |

      - oracle：支持2种事务隔离级别 读已提交(Read Committed)和串行化。Oracle默认的事务隔离级别为读已提交。

      - Mysql支持4种事务隔离级别，Mysql默认的事务隔离级别是可重复读

- 视图


  - 就是一个虚拟表，和普通的表使用的方法是一样的，是通过表动态生成的数据，mysql5.1版本中出现的，是具有临时性的特点。

  - Mysql从5.1版本开始提供试图功能，一种虚拟存在的表，行和列的数据来自定义视图的查询中使用的表，并且是在使用视图时动态生成的，只保存啦sql逻辑，不保存查询结果。

  - 应用场景：


    - 多个地方用到同样的查询结果。
    - 该查询结果使用sql语句比较复杂。

  - 语法：


~~~sql
- create view 视图名字 as 查询语句。

- ```sql
  #使用视图
  create or replace view myv2
    as
    select avg(salary) as ag ,e.department_id from employees e group by  e.department_id;
   #链接视图
   select * from myv2 m left join job_grades g on m.ag between g.lowest_sal and g.highest_sal;
  ```

- 视图的好处：

  - 重用sql
  - 简化复杂的sql操作,不必知道他的查询细节。
  - 保护数据提高安全性

- 视图的修改

- 语法：

  - ```sql
    #方式一
    create or replace 视图名字
    as 查询语句。
    #方式二
    alter view 视图名字 查询语句。
    
    ```

- 视图的删除

  - 语法：

    - ```sql
      #可以同时删除多个视图
      drop view 视图名字1,视图名字2,视图名字3...
      
      ```

- 查询视图结构

  - ```sql
    #查看视图的结构。
    desc 视图名字
    ```

  -
~~~
- 一般是不可以对视图进行增删改的操作的。

- 视图的可更新性和视图中查询的定义有关系，以下的类型视图是不可以更新的。

  - 包含以下关键字的sql语句，分组函数，distinct ,group by ,having union或者union all

  - ```sql
    create or replace view my_v9
      as
      select max(salary),department_id from employees group by department_id;
    ```

  - 常量视图

  - ```sql
    create or replace view my_v9
      as
      select max(salary),department_id from employees group by department_id;
    ```

  - Select 中包含子查询

  - ```sql
    create or replace  view my_v11
      as
      select (select max(salary) from employees )最高工资;
    ```

  - join 

    ```sql
    select e.last_name,d.department_name from employees e left join departments d on e.department_id = d.department_id;
    
    ```

  - from 一个不能更新的视图

    ```sql
    create or replace view my_v13
      as
      select * from employees;
    ```

  - where 子句的子查询引用了from子句中的表。

    - ```sql
      create or replace view my_v14
        as
        select last_name,email ,salary from employees where employee_id in(
          select manager_id from departments d where d.manager_id is not null);
      ```

  - Delete 和 truncate的区别：

    - ```sql
      #delete 在回滚之后数据不被删除
      set autocommit = 0; 设置手动提交
      start transaction;  开启事务
      delete from departments; 执行sql语句
      rollback ;#回滚
      
      #在回滚之后数据依然被删除
      set autocommit =0;#设置手动提交
      start transaction ;#开启事务
      truncate table  departments;#执行sql语句
      rollback ;	#回滚
      ```

    - 