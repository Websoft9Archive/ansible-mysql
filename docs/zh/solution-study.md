# MySQL速学

## MySQL 使用入口

镜像安装完成后，MySQL就可以使用了。使用MySQL有两种方式方式

### 方式一 图形工具

镜像提供了可视化的界面：如MySQL-Front，phpMyAdmin。也可以开启远程链接后，在本地使用Navicat访问

### 方式二 命令方式

使用Putty远程登录到Linux服务器（或远程桌面登录到Windows-CMD窗口），运行命令

~~~
#假设初始密码是：123456
mysql -uroot –p123456
~~~

## 常见命令

### 创建/删除/查看数据库

创建一个数据库

mysql -uroot  –p密码                                        #进入数据库控制台

MySQL [(none)]> create database 数据库名称;     #特别注意有分号

MySQL [(none)]>  show  databases;                      #查看数据库

MySQL [(none)]>  exit;                                 #退出数据库控制台，特别注意有分号

删除一个数据库

MySQL [(none)]> drop database 数据库名称;     #删除数据库

MySQL [(none)]> exit;                                     #退出数据库控制台，特别注意有分号

查看数据库: show databases;           #如下图中3个数据库是默认数据库，不可删除

![websoft9-mysql](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/mysql_databases_default.png)

选择数据库: use dbname;

### 表的操作

显示库下面的表
show tables;

查看表的结构:
desc tableName;

查看表的创建过程:
show create table tableName;

创建表:
create table tbName ( 列名称1　列类型　[列参数]　[not null default ], ….列2… …. 列名称N　列类型　[列参数]　[not null default ] )engine myisam/innodb charset utf8/gbk

例子:
create table user ( id int auto_increment, name varchar(20) not null default ”, age tinyint unsigned not null default 0, index id (id) )engine=innodb charset=utf8;
注:innodb是表引擎,也可以是myisam或其他,但最常用的是myisam和innodb,
charset 常用的有utf8,gbk;

修改表
1.修改表之增加列:
alter table tbName add 列名称１　列类型　[列参数]　[not null default ]　#(add之后的旧列名之后的语法和创建表时的列声明一样)

2.修改表之修改列
alter table tbName change 旧列名 新列名 列类型　[列参数]　[not null default ]
(注:旧列名之后的语法和创建表时的列声明一样)

3.修改表之减少列:
alter table tbName drop 列名称;

4.修改表之增加主键
alter table tbName add primary key(主键所在列名);
例:alter table goods add primary key(id)
该例是把主键建立在id列上

5.修改表之删除主键
alter table tbName　drop primary key;

6.修改表之增加索引
alter table tbName add [unique|fulltext] index 索引名(列名);

7.修改表之删除索引
alter table tbName drop index 索引名;

8.清空表的数据
truncate tableName;

### 表数据操作

1.插入数据 
	insert into 表名(col1,col2,……) values(val1,val2……); -- 插入指定列
	insert into 表名 values (,,,,); -- 插入所有列
	insert into 表名 values	-- 一次插入多行 
	(val1,val2……),
	(val1,val2……),
	(val1,val2……);

2.修改数据
	update tablename 
	set 
	col1=newval1,  
	col2=newval2,
	...
	...
	colN=newvalN
	where 条件;

3.删除数据    delete from tablenaeme where 条件;

4.select查询

  （1）  条件查询   where  a. 条件表达式的意义，表达式为真，则该行取出
			   b.  比较运算符  = ，!=， =
                           c.  like , not like ('%'匹配任意多个字符,'_'匹配任意单个字符) 
				in , not in , between and
                           d. is null , is not null			
  （2）  分组       group by 
			一般要配合5个聚合函数使用:max,min,sum,avg,count
  （3）  筛选       having
  （4）  排序       order by
  （5）  限制       limit

5.连接查询
5.1 左连接
	.. left join .. on
	table A left join table B on tableA.col1 = tableB.col2 ; 
  例句:
  select 列名 from table A left join table B on tableA.col1 = tableB.col2

5.2 右链接: right join

5.3 内连接: inner join 左右连接都是以在左边的表的数据为准,沿着左表查右表. 内连接是以两张表都有的共同部分数据为准,也就是左右连接的数据之交集. 7 子查询 where 型子查询:内层sql的返回值在where后作为条件表达式的一部分 例句: select * from tableA where colA = (select colB from tableB where ...); from 型子查询:内层sql查询结果,作为一张表,供外层的sql语句再次查询 例句:select * from (select * from ...) as tableName where ....

## 关于 test 数据库
在MySQL5.7 版本之前，安装 MySQL 时会默认包含一个 test 数据库，该数据库仅仅用来测试使用，但是所有能连接到MySQL的用户，几乎都拥有test库的所有权限，因此存在一定的安全隐患。从信息安全角度考虑，如果您发现您使用的 MySQL 中有该 test 数据库，请**务必删除**。