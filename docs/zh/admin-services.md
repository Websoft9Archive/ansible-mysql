# 服务启停

使用由 Websoft9 提供的 MySQL 部署方案，可能需要用到的服务如下：

## Linux系统

### MySQL
```shell
#For CentOS&Redhat
sudo systemctl start mysqld
sudo systemctl restart mysqld
sudo systemctl stop mysqld
sudo systemctl status mysqld

#For Ubuntu&Debian
sudo systemctl start mysql
sudo systemctl restart mysql
sudo systemctl stop mysql
sudo systemctl status mysql
```

### MariaDB
```shell
systemctl start mariadb
systemctl stop mariadb
systemctl restart mariadb
```

### Docker

```shell
sudo systemctl start docker
sudo systemctl restart docker
sudo systemctl stop docker
sudo systemctl status docker
```

## Windows 系统

Windows下的镜像采用操作系统的服务管理功能，来实现 MySQL 的启动、停止和重启操作

![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/mysql-servicewin-websoft9.png)