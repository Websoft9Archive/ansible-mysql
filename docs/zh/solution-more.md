# 更多...

下面每一个方案，都经过实践证明行之有效，希望能够对你有帮助

## 更换MySQL数据目录

The data directory for MySQL is set to */data/mysql* by default. If you want to modify MySQL Data Directory, following are the steps for you:

1. Stop the MySQL Service
   ```shell
   sudo sytemctl stop mysqld
   ```
2. Move the */data/mysql* to the destination directory, e.g */data/mysql2* 
3. Modify the location of this folder modifying the`/etc/my.cnf` file, as shown below:
   ```shell
   datadir=/data/mysql2
   ```
4. Restart the MySQL
   ```shell
   sudo sytemctl start mysqld
   ```


## 设置 Binary Log

The binary log contains "event" that describe database changes such as table creation operations or changes to table data. It also contains events for statements that potentially could have made changes (for example, a DELETE which matched no rows), unless row-based logging is used. The binary log also contains information about how long each statement took that updated data. 

### Binary log configuration

You can modify the MySQL configuration _/etc/my.cnf_ to change the binary log settings

```
log_bin = mysql-bin      # enable Binary log
binlog_format = mixed    # Binary log format
expire_logs_days = 7     # Binary log expire time
```

### Binary log file size
Some times, there a lot of event for your database, then the binary log file size very rapid growth and your disk space may not enough, if there no space on disk, your MySQL Service can not start.

Suggest you change the expire_logs_day to more smaller if you binary log file size is too big

## 权限设置