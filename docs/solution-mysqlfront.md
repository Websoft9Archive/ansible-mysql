# GUI:MySQL-Front

MySQL-Front是一款小巧的管理Mysql的应用程序。下面介绍常见的MySQL-Front操作。

## 远程连接MySQL

1. 打开MySQL-Front，点击顶部菜单栏， 【文件】>【连接管理】
     ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/websoft9-mysql-fronttest.png)

2. 自定义连接名，主机为数据库所在的主机ip地址（[不知道账号密码？](/zh/stack-accounts.md)）
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/websoft9-mysql-frontcome.png)

3. 点击“确定”后，在连接管理窗口上点击“打开”，系统无任何提示及警告即表示连接成功

## 新增数据库

1. 登录数据库

2. 在连接管理窗口上点击“打开”，一个新的数据库变建立成功

3. 登录成功进入到数据库操作界面，该界面为图形化操作，方便、简洁
  ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/websoft9-mysql-frontteacher3.png)

> 注意：可以在本地导入数据库，此次操作导入数据库名为mysql。

## 数据库导入和导出

导入即恢复数据库，导出即备份数据库。这个两个操作对SQL-Front来说比较简单，具体如下：

1. 登录数据库

2. 右击你选择的数据库名，完成：【导入】>【SQL文件】，选择本地已有的*.sql数据库备份文件
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/websoft-mysql-frontcome2.png)

3. 点击上方导航栏的大的绿色按钮即可执行

  >注意：根据实际情况选择默认的字符集，一般选择UTF-8

4. 选择备份的数据库，右击你选择的数据库名，依次完成：【导出】>【SQL文件】，完成数据库备份

## 运行SQL语句
 
点击工具栏中：【视图】>【SQL编辑器】，手动编写SQL语句并执行