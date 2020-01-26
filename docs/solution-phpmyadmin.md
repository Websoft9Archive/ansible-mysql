# GUI:phpMyAdmin

phpMyAdmin is a very popular MySQL database management tool. The following describes the common phpMyAdmin operations.

### Log in to phpMyAdmin

1. Open Chrome or Firefox on your local PC to visit the _phpMyAdmin_,you can enter the login page  
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/en/mysql/mysql-login-websoft9.png)
2. Select you language, Username is `root`,Password should get from the Chapter"[Administrator usenames and password](stack-accounts)"
3. Click the button "Go"

### Modify the root password

1. Login to phpMyAdmin, you can see the "Modify the password" link in dashboard page, then click it
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/en/phpmyadmin/phpmyadmin-changepwds-websoft9.png)

2. After the modification of password, exit phpMyAdmin and refresh the log in page to restart it

### Add new database

1. Login to phpMyAdmin, click "New" in the left menu to start creating a new database
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/en/phpmyadmin/phpmyadmin-createdb-websoft9.png)

2. Fill in the suitable Database Name, select the character coding, then click "Create" button to complete this step

### Add user account

> The database user is separated from the database and is a "many-to-many" relationship. You can associate a user with the permissions of a database by associating


1. Login to phpMyAdmin, Click one database on the left menu which you want to add user account for it
2. Click "**Privileges**" tab, you can see the users belong to this database listed
3. Click "**Add user account**", start to add new user
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/mysql/mysql-adduser-websoft9.png)

4. Fill in suitable User name/Host name/Password, click "go" button to complete this step
5. You can also go to User account->Add user account to manage users