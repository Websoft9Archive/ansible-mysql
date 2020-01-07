# MySQL 修改或重置密码

修改密码，即使用已有密码登录MySQL，然后修改成另外一个密码  
重置密码，即忘记了密码，需要通过重置密码找回

## 修改密码

可以通过MySQL管理工具修改密码，也通过命令上修改密码

### 管理工具修改密码

* phpMyAdmin修改密码
![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/websoft9-modifymysqlpw.gif)
* MySQL-Front修改密码

### 命令行修改密码

执行一下命令:
```
mysqladmin -u 用户名 -p 密码 password '需要修改得密码' 
```

## 重置密码

## 快捷方案

1. 远程连接到服务器，
2. 运行一下命令，按提示输入新密码即可。

   ```

   sudo git clone https://github.com/Websoft9/linux.git; cd linuxscript/Mysql\_ResetPasswd\_Script;sudo sh reset\_mysql\_password.sh

   ```
## 原理

如果忘记了root密码，就需要通过命令操作，实现MySQL密码重置：

1. 停止 MySQL 服务
   
   ~~~
    systemctl stop mysqld
   ~~~
   
2. 采用命令行参数启动mysql 
   
   ~~~
    mysqld_safe --skip-grant-tables &
   ~~~
   
3. 重置密码（这里将密码重置为`123456`）
   
   ~~~
   mysql -e "use mysql;update user set password=password('123456') where user='root';"
   ~~~
   
4. 关闭MySQL进程
    
    ~~~
    killall mysqld
    ~~~ 
    
5. 启动MySQL服务
  
   ~~~
   systemctl start mysqld
   ~~~