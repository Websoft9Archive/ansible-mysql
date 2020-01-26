# GUI:jspMyAdmin

下面介绍常见的JspMyAdmin操作

## JspMyAdmin 修改密码
1. 在浏览器上输入*http://服务器公网IP/jspmyadmin*，，进入jspMyAdmin管理界面

2. 登录 jspMyAdmin（[不知道账号密码？](/zh/stack-accounts.md)）

3. 点击上方菜单栏“ Users & Privileges ,在下方显示的页面单击“alter user”
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/jspmyadmin-updatepw2-websoft9.png)

4. 输入新的密码，最后点击“run”即可
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/jspmyadmin-updatepw1-websoft9.png)

   >注意，在修改密码的过程中，必须将服务器上所有密码一并重置修改，操作三次密码修改才能保证密码重置成功

## JspMyAdmin 开启MySQL远程

1. 登录到 jspMyAdmin

2. 点击上方菜单栏“ Users & Privileges” ,在下方显示的页面单击“alter user”，将Host Name文本框中“localhost”更改为“%”
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/jspmyadmin-updatehost-websoft9.png)
    
   >注意，在远程连接的过程中，只需更改原主机名为“localhost”的服务器为“%”即可

## JspMyAdmin 导出数据

1. 登录到 jspMyAdmin

2. 点击上方菜单栏“ Export”，此时 JspMyAdmin 会自动添加你刚创建的所有数据库，单击“run”导出完成
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/jspadmin-exportmath-websoft9.png)
   
   >说明：如果没有可以导出的数据库，可以在左侧的数据库名上右健`新建--数据库`，进行创建

