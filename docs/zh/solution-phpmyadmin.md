# 图形化工具：phpMyAdmin

phpMyAdmin是很受欢迎的MySQL数据库管理工具，下面介绍常见的phpMyAdmin操作

## 修改root密码

1. 登录phpMyAdmin后，默认页面-常规设置，点击“修改密码” ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/phpmyadmin-modifypw-websoft9.png)
2. 修改密码-&gt;保存-&gt;退出登录，刷新浏览器后便可以使用新密码登录了

## 新增数据库

1. 登录phpMyAdmin后，点击左侧菜单栏的“新建”，进入如下的数据库创建界面 ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/phpmyadmin-adddb-websoft9.png)
2. 填写数据库名-&gt;点击创建按钮，一个新的数据库变建立成功
3. 默认情况下，root拥有新建的数据库的全部权限

## 新增数据库用户

> 数据库用户与数据库是分离的，是“多对多”的关系。可以通过关联使得某个用户具有某个数据库的权限

1. 登录phpMyAdmin后，点击左侧菜单栏中新打算对其新增用户的数据库（例如：mywebsoft9）
2. 点击顶部菜单栏的“权限”，找到“新增用户账户”，如下新增用户界面 ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/phpmyadmin-adduser-websoft9.png)
3. 根据上图填写用户名、主机地址和密码，然后关联对应的数据库和勾选权限设置
4. 点击“执行”，就完成新增用户和数据库关联了

说明：也可以登录phpMyAdmin的默认页面后，点击顶部菜单上“账户”，对用户和权限进行管理

## 数据库导入和导出

> 导出即备份数据库，导入即恢复数据库。这个两个操作对phpMyAdmin来说比较简单，具体如下：

1. 登录phpMyAdmin后，选择您需要操作的数据库后，点击顶部菜单栏的“导出” ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/phpmyadmin-export-websoft9.png)
2. 选择导出方式（默认为“快速”）和格式（默认为“SQL”），点击“执行”按钮
3. 数据库备份文件（.sql后缀）生成后，保存到本地完成导出工具
4. 恢复数据库，对应的是“导入”操作，具体参考下图 ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/phpmyadmin-import-websoft9.png)
5. 导入文件特别要注意字符集兼容性

## 常见问题

#### phpMyAdmin on Docker如何修改导入文件大小限制？

1. 使用 SFTP 连接服务器，编辑 */data/apps/phpmyadmin/docker-compose.yml* 文件，在环境变量处增加一个字段 `- UPLOAD_LIMIT=20M`
  ```
  version: "3.7"
  services: 
    phpmyadmin:
        image: phpmyadmin/phpmyadmin
        container_name: "phpmyadmin"
        environment:
         - PMA_HOST=172.17.0.1
         - PMA_PORT=3306
         - UPLOAD_LIMIT=20M
  ```

2. 重新创建 phpMyAdmin 容器后生效
  ```
  cd /data/apps/phpmyadmin && docker-compose up -d
  ```


#### phpMyAdmin 限制特定 IP 访问

把 phpMyAdmin.conf（```/etc/httpd/conf.d/phpmyAdmin.conf```）文件中的：  
     ```Require all granted``` 
改为：  
     ```Require ip xxx.xxx.xxx.xxx```  
这样，只有指定 IP 的主机能访问 phpMyAdmin，IP还可以缩写：192.168.*.* 这样则表示以 192.168 开头的 IP 段都能访问。 修改完成后需要重启 Apache
