# MySQL remote connection

当你想通过本地的电脑的MySQL客户端（例如：Navicat）连接服务器上的MySQL的时候，就需要设置 MySQL 的远程访问。

数据库是高安全应用，设置远程访问，最少两个独立的步骤：

## 安全组放通3306端口

一般来说，MySQL使用的是3306端口。

首先，我们要登录到云控制台，打开云服务器所在的安全组中，保证3306端口是开启的。

![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/mysql3306-websoft9.png)


## 开启MySQL远程连接

安全组开启后，还没有完成MySQL远程方案的设置。  

接下来，还需要对 MySQL 自身进行设置，以便其接受外部网络的访问

我们提供两种开启MySQL的远程连接的方案，第一种是可视化方式，第二种是命令方式：  

#### 可视化开启（推荐）

在phpMyAdmin中开启远程只需要将root账号的访问方式改成“任意方式访问”，具体如下：

1. 打开账户->找到主机名为127.0.0.1的root用户，点击“修改权限”
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/mysql-openremote001-websoft9.png)
2. 在“登录信息”选项卡中，将“主机名”下拉菜单选项更改为“任意主机”，点击执行
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/mysql-openremote002-websoft9.png)
3. 以上两步就完成了开启远程连接的工作

#### 命令开启

如果您的镜像中没有安装phpMyAdmin，那么就需要通过命令方式开启远程连接。具体如下：

1. 使用SSH连接到服务器，登录到MySQL
   ```
   mysql -u root -p 数据库root密码
   ```
 
2. 写入SQL语句,开启远程访问
   ```
   mysql>  use mysql;
   mysql>  update user set host = '%' where user = 'root';
   ```

3. 运行下面的语句，查看设置是否生效（显示%的值）
   ```
   select host,user from user where user='root'
   ```
4. 退出MySQL命令，回到Linux命名模式，重启MySQL
   ```
   systemctl restart mysqld
   ```
   > 本步骤是必须的，否则在用Navicat Premium/MySQL-Front等工具测试远程的时候会报错误信息