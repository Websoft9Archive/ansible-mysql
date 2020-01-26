# Parameters

The MySQL deployment package contains a sequence software (referred to as "components") required for MySQL to run. The important information such as the component name, installation directory path, configuration file path, port, version, etc. are listed below.

## Path
You should know the components is different for different OS before using MySQL/MariaDB

### Linux

#### MySQL&MariaDB

MySQL install directory: */usr/share/mysql*  
MySQL data directory: */data/mysql*  
MySQL Configuration File: */etc/my.cnf*  
MySQL error log: */var/log/mysql/mysqld.log*  
MySQL Process Identification Number: */run/mysqld/mysqld.pid*  
MySQL Socket: */var/lib/mysql/mysql.sock*  

#### phpMyAdmin on Docker

Most of time, we used Docker to install phpMyAdmin

#### phpMyAdmin on PHP

For php runtime, e.g LAMP/LNMP, phpMyAdmin is an application for deployment   

phpMyAdmin installation directory: */data/apps/phpmyadmin*  
phpMyAdmin configuration file: */data/apps/phpmyadmin/config.inc.php*   
phpMyAdmin vhost configuration file: */etc/httpd/conf.d/phpMyAdmin.conf*   

### Windows Sever

#### MySQL&MariaDB

Database install directory: */C:/websoft9/mysql*  
Database data directory: */C:/websoft9/mysql/data*  
Database configuration file: */C:/websoft9/mysql/my.ini*  


## Ports

You can control(open or shut down) ports by **[Security Group Setting](https://support.websoft9.com/docs/faq/tech-instance.html)** of your Cloud Server whether the port can be accessed from Internet.

These ports should be opened for this application:

| Name | Number | Use |  Necessity |
| --- | --- | --- | --- |
| phpMyAdmin on Docker | 9090 | HTTP to visit phpMyAdmin | Optional |
| MySQL | 3306 | remote connect MySQL | Optional |
| MariaDB | 3306 | remote connect MariaDB | Optional |

## Version

You can see the version from product page of Marketplace. However, after being deployed to your server, the components will be automatically updated, resulting in a certain change in the version number. Therefore, the exact version number should be viewed by running the command on the server:

```shell
# Linux Version
lsb_release -a

# MySQL version
mysql -V

# MySQL Version
docker -v
```