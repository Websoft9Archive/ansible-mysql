# GUI: Workbench

Once your MySQL server is configured to accept remote connections, you can connect to it using MySQL Workbench. Follow these steps:

- Launch MySQL Workbench.

- Click the "+" symbol in the "MySQL Connections" tab to add a new connection.

![](https://docs.bitnami.com/images/img/components/mysql/mysql-mwb-1.png)

- Configure the connection as follows:
  - Enter a name for the connection in the "Connection Name" field.
  - Select "Standard (TCP/IP)" as the "Connection Type".
  - Enter your cloud server's IP address in the "Hostname" field.
  - Specify the "Port" as "3306".
  - Specify the "Username" as "root".

![](https://docs.bitnami.com/images/img/components/mysql/mysql-mwb-2.png)

- Click "Test Connection" to test the connection.

- If the connection is successful, click "OK" to save the connection.

![](https://docs.bitnami.com/images/img/components/mysql/mysql-mwb-3.png)

- Double-click the new connection to launch the MySQL Workbench SQL Editor. You may be prompted for a password. Use the same password you used when previously configuring the server to accept remote connections. Once connected, the SQL editor window will open and you can interact with the server using SQL commands, as shown below:

![](https://docs.bitnami.com/images/img/components/mysql/mysql-mwb-4.png)