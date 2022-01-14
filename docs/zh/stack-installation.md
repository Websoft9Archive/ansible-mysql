# 初始化验证

在云服务器上部署 MySQL 预装包之后，请参考下面的步骤快速入门。

## 准备

1. 在云控制台获取您的 **服务器公网IP地址** 
2. 如果想从本地客户端远程连接 MySQL，登录云控制台安全组中，检查 **Inbound（入）规则** 下的 **TCP:3306** 端口是否开启
3. 如果想使用可视化管理工具 phpMyAdmin，登录云控制台安全组中，检查 **Inbound（入）规则** 下的 **TCP:9090** 端口是否开启

## MySQL 初始化验证

部署 MySQL 之后，依次完成下面的步骤，验证其可用性

### 检测 MySQL 安装

1. 使用 SSH 连接 MySQL 所在的服务器，运行下面的命令，查看 MySQL 的安装信息和运行状态
   ```
   sudo systemctl status mysqld
   或
   sudo systemctl status mysql
   ```
2. 运行服务状态查询命令，MySQL 正常运行会得到 " Active: active (running)... " 的反馈

镜像安装完成后，MySQL就可以使用了。使用MySQL有两种方式方式

### 命令方式连接 MySQL

1. 使用Putty远程登录到Linux服务器（或远程桌面登录到Windows-CMD窗口），运行命令
   ~~~
   #假设初始密码是：123456
   mysql -uroot –p123456
   ~~~

2. 查看反馈的信息中MySQL版本
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/en/mysql/mysql01.png)

### MySQL 主从配置

如果您购买了两台MySQL主从服务器，按照如下步骤可实现所有库、表等数据同步：

1. 使用SSH工具远程登录到MySLQ master 服务器，运行命令查看脚本帮助
   ~~~
   cd /data/config
   [root@iZbp1914ntfd3d0jadprbyZ tools]# bash master.sh -h

     -h, --help      show help information
     -M, --master-root-password  master mysql root password, Required parameter
     -u, --slave-username   slave mysql username, Required parameter
     -s, --slave-password   slave mysql password, Required parameter
     example:
       bash master.sh -M 123456 -u slave -s 123456
   
   ~~~

2. 根据上面的帮助命令，将-M的参数"123456"替换成数据库root密码([不知道密码？](/zh/stack-accounts.md#mysql))
   ```
   [root@iZbp1914ntfd3d0jadprbyZ tools]# bash master.sh -M T9M9bouSVAR9s7m -u slave -s 123456
   master mysql root password is: T9M9bouSVAR9s7m
   slave mysql username is: slave
   slave mysql password is: 123456
   Get parameters success !
   mysql config file update success !
   mysql: [Warning] Using a password on the command line interface can be insecure.
   mysql: [Warning] Using a password on the command line interface can be insecure.
   Create mysql user and set permissive success !
   mysql: [Warning] Using a password on the command line interface can be insecure.
   mysql: [Warning] Using a password on the command line interface can be insecure.
   mysql: [Warning] Using a password on the command line interface can be insecure.
   master log file is: mysql-bin.000008
   master log pos is: 817
   --------------------------------------------
   Congratulations, run complete.
   --------------------------------------------
   [root@iZbp1914ntfd3d0jadprbyZ tools]# 

   ```
   
### phpMyAdmin 连接 MySQL

如果部署方案中包含 phpMyAdmin 等图形化工具，使用就更加便捷方便：

1. 本地浏览器 Chrome 或 Firefox 访问：*http://服务器公网IP:9090*，进入phpMyAdmin
  ![登录phpMyadmin](https://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/phpmyadmin-logincn-websoft9.png)
2. 输入数据库用户名和密码([不知道密码？](/zh/stack-accounts.md#mysql))
3. 开始管理数据库
  ![phpMyadmin](https://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/phpmyadmin-adddb-websoft9.png)

> 需要了解更多 phpMyAdmin 的使用，请参考本文档 [phpMyAdmin 章节](/zh/solution-phpmyadmin.md)

## 常见问题

#### 浏览器无法访问 phpMyAdmin（白屏没有结果）？

您的服务器对应的安全组9090端口没有开启（入规则），导致浏览器无法它

#### phpMyAdmin 是如何安装的？

采用 Docker 安装，保证 MySQL 环境具有良好的隔离性。
