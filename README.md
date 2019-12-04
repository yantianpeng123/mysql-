mysql—知识点总结

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

  -  like特点：

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

    - 