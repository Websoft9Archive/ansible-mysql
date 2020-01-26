# MySQL速学


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
