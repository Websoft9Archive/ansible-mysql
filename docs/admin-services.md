# Start or Stop the Services

These commands you must know when you using the MySQL of Websoft9

## Linux

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

## Windows

For Windows Sever, please use the system's services management to start | stop | restart MySQL  
![](https://libs.websoft9.com/Websoft9/DocsPicture/en/mysql/mysql-servicewin-websoft9.png)