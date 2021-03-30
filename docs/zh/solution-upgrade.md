# 更新升级

网站技术日新月异，**更新升级**是维护工作之一，长时间不升级的程序，就如长时间不维护的建筑物一样，会加速老化、功能逐渐缺失直至无法使用。  

这里注意更新与升级这两词的差异（[延伸阅读](https://support.websoft9.com/docs/faq/zh/tech-upgrade.html#更新-vs-升级)），例如：  

- 操作系统打个补丁常称之为**更新**，Ubuntu16.04 变更为 Ubuntu18.04，称之为**升级**
- MySQL5.6.25-->MySQL5.6.30 常称之为**更新**，MySQL5.6->MySQL5.7 称之为**升级**

MySQL 完整的更新升级包括：系统级更新（操作系统和运行环境）和 MySQL 程序升级两种类型

## 系统级更新

运行一条更新命令，即可完成系统级更新：

``` shell
#For Ubuntu&Debian
apt update && apt upgrade -y

#For Centos&Redhat
yum update -y
```
> 本部署包已预配置一个用于自动更新的计划任务。如果希望去掉自动更新，请删除对应的Cron

## MySQL 更新升级

### On Linux

上面的系统升级命令，支持小版本升级。例如：5.6.x to 5.6.y 或 5.7.x to 5.7.y

数据库大版本之间的差异较大，无法提供稳妥的升级方案

### On Windows

MySQL upgrade on Windows Server divided into two parts

1. Use Windows Update to upgrade Windows System
2. Dowload the lastest MySQL, stop the MySQL Services and replace the old files of MySQL

## phpMyAdmin 更新升级

不同的 phpMyAdmin 安装方式，对应不同的升级方案：

### phpMyAdmin on Docker

Docker 版 phpMyAdmin 只需到 phpMyAdmin 的目录下，运行 docker-compose 命令即可升级：

```
cd /data/apps/phpmyadmin
docker-compose pull
docker-compose up -d
```

### phpMyAdmin 普通安装

若通过 *http://服务器公网IP/phpmyadmin* 访问，则表示是通过普通的 PHP 应用程序的方式。  

对应的升级方案：  

1. 检查服务器上的 PHP 版本是否满足最新的 [phpMyAdmin](https://www.phpmyadmin.net/) 之要求

2. 备份旧版本到 */data/apps/phpmyadminBK* 文件夹

3. 下载版本 [phpMyAdmin](https://www.phpmyadmin.net/) 并覆盖 phpmyadmin 安装目录（目录名称与旧版本一致 ）

4. 设置用户和组和访问权限
   ```
   #更改文件夹用户权限
   chmod  -R 750 phpmyadmin
   #更改用户和组
   chown  -R apache:apache phpmyadmin
   ```
5. 备份目录中的配置文件 config.inc.php 拷贝正式目录

6. 测试安装结果


## 常见问题

#### 大版本升级后，无法更改数据库密码？
```
mysql_upgrade -u root -p 13456
```
