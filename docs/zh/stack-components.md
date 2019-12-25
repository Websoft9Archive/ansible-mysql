# 参数

MySQL 预装包包含 MySQL 运行所需一序列支撑软件（简称为“组件”），下面列出主要组件名称、安装路径、配置文件地址、端口、版本等重要的信息。

## 路径

### Linux

#### MySQL

MySQL 根目录: */var/lib/docker*  
MySQL 镜像目录: */var/lib/docker/image*   
MySQL daemon.json 文件：默认没有创建，请到 */etc/docker* 目录下根据需要自行创建   

#### phpMyAdmin on Docker

对于单独的 MySQL 预装包以及非PHP程序来说，phpMyAdmin 是采用 Docker 的方式来安装的

Portainer 数据卷：*/var/lib/docker/volumes/portainer_data/_data*   

#### phpMyAdmin on PHP

对于 PHP 环境预装包来说（例如：LAMP/LNMP等），phpMyAdmin 是作为一个 PHP 应用程序来安装的

### Windows

* 目录：C:/websoft9/mysql
* 配置文件：C:/websoft9/mysql/etc/my.ini
* 数据文件目录:：C:/websoft9/mysql/data
* 默认用户/密码：`root/123456` 

> 如果是mariadb镜像，以上路径mysql替换即可

## 端口号

在云服务器中，通过 **[安全组设置](https://support.websoft9.com/docs/faq/zh/tech-instance.html)** 来控制（开启或关闭）端口是否可以被外部访问。 

本应用建议开启的端口如下：

| 名称 | 端口号 | 用途 |  必要性 |
| --- | --- | --- | --- |
| phpMyAdmin on Docker | 9000 | 通过 HTTP 访问 phpMyAdmin | 可选 |
| MySQL | 3306 | 远程连接MySQL | 可选 |

## 版本号

组件版本号可以通过云市场商品页面查看。但部署到您的服务器之后，组件会自动进行更新导致版本号有一定的变化，故精准的版本号请通过在服务器上运行命令查看：

```shell
# Linux Version
lsb_release -a

# MySQL version
mysql -V

# MySQL Version
docker -v
```