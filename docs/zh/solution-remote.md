# 设置 MySQL 远程访问

当你想通过本地的电脑的MySQL客户端（例如：Navicat）连接服务器上的MySQL的时候，就需要设置 MySQL 的远程访问。

数据库是高安全应用，需要两个步骤，才能正真被远程访问：

## 安全组放通3306端口

一般来说，MySQL占用的是3306端口，需通过在云服务器的控制台-安全组中，开启它。

![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/mysql3306-websoft9.png)


## 开启MySQL远程连接

开启MySQL远程连接，是对MySQL自身进行设置，我们提供两种方式可以开启MySQL的远程连接。

第一种是可视化方式，第二种是命令方式：  

#### 可视化开启远程连接（推荐）

在phpMyAdmin中开启远程只需要将root账号的访问方式改成“任意方式访问”，具体如下：

1. 打开账户->找到主机名为127.0.0.1的root用户，点击“修改权限”
![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/mysql-openremote001-websoft9.png)
2. 在“登录信息”选项卡中，将“主机名”下拉菜单选项更改为“任意主机”，点击执行
![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/mysql-openremote002-websoft9.png)
3. 以上两步就完成了开启远程连接的工作

#### 命令开启远程连接

如果您的镜像中没有安装phpMyAdmin，那么就需要通过命令方式开启远程连接。具体如下：

1. 执行命令,进入数据库
    命令:  `mysql -u root -p 数据库root密码`
 
2. 写入SQL语句,开启远程访问
    mysql>  `use mysql;`
    mysql>  `update user set host = '%' where user = 'root';`
  
  
   >  注意: 第二条语句可能会报错误信息, 可以忽略,实际语句已经生效, 可以输入语句     select host,user from user where user='root'; 进行查看host值是否有"%"
   >  RROR 1062 (23000): Duplicate entry '%-root' for key 'PRIMARY' 
   >  说明有多个ROOT用户纪录在USER表中了.
 
 3. 退出MySQL命令，回到Linux命名模式，重启MySQL
     命令：  `systemctl restart mysqld`
     
     >  注意：在用Navicat Premium/MySQL-Front等工具测试远程连接前，必须重启数据库，否则会报错误信息
     
 4. 打开服务器控制台上的安全组端口TCP:3306