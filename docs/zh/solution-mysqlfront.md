# 图形化工具：MySQL-Front

MySQL-Front是一款小巧的管理Mysql的应用程序.主要特性包括多文档界面，语法突出，拖拽方式的数据库和表格。可编辑/可增加/删除的域，可编辑/可插入/删除的记录，可显示的成员，可执行的SQL 脚本，提供与外程序接口，保存数据到CSV文件等。下面介绍常见的MySQL-Front操作。

## 远程连接MySQL

1. 打开MySQL-Front，点击顶部菜单栏， `文件->连接管理`
     ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/websoft9-mysql-fronttest.png)

2. 自定义连接名，主机为数据库所在的主机ip地址，密码默认**123456**

3. 点击“确定”后，在连接管理窗口上点击“打开”，系统无任何提示及警告即表示连接成功

## 新增数据库

1. 打开MySQL-Front后，点击左侧菜单栏的`文件->连接管理`，弹出如下窗口，
     ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/websoft9-mysql-fronttest.png)
  2. 自定义连接名，主机为数据库所在的主机ip地址，密码默认**123456**
    ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/websoft9-mysql-frontcome.png)
  4. 点击“确定”后，在连接管理窗口上点击“打开”，一个新的数据库变建立成功
  5. 登录成功进入到数据库操作界面，该界面为图形化操作，方便、简洁
![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/websoft9-mysql-frontteacher3.png)

>注意：可以在本地导入数据库，此次操作导入数据库名为mysql。

## 数据库导入和导出

> 导入即恢复数据库，导出即备份数据库。这个两个操作对SQL-Front来说比较简单，具体如下：

1. 右击你选择的数据库名`导入->SQL文件 `，首先我们本地有个*.sql数据库备份文件（.sql的文件最好也是MySQL-Front软件备份出来,这样导入不容易出错）
 ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/websoft-mysql-frontcome2.png)
 
>说明：我们也可以点击工具栏中`视图-SQL编辑器`手动编写sql语句并可以执行
>注意：根据实际情况选择默认的字符集，一般utf-8即可

2. 点击上方导航栏的大的绿色按钮即可执行

>注意：在执行的时候，如果是要创建数据库请查看脚本里面是否有创建数据库的脚本，如果没有则在左侧的ip地址上面右健`新建--数据库`，进行创建

3. 我们用MySQL-Front备份数据库时，首先连接需要备份的数据库，右击你选择的数据库名`导出->SQL文件`


>注意：在导入导出数据库的同时，等待页面加载完成并没错误就可以关闭页面