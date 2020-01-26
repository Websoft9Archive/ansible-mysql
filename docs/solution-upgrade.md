# Update & Upgrade

Updates and upgrades are one of the maintenance tasks for system. Programs that are not upgraded for a long time, like buildings that are not maintained for a long time, will accelerate aging and gradually lose functionality until they are unavailable.

You should know the differences between the terms **Update** and **Upgrade**([Extended reading](https://support.websoft9.com/docs/faq/tech-upgrade.html#update-vs-upgrade))
- Operating system patching is **Update**, Ubuntu16.04 to Ubuntu18.04 is **Upgrade**
- MySQL5.6.25 to MySQL5.6.30 is **Update**, MySQL5.6 to MySQL5.7 is **Upgrade**

For MySQL maintenance, focus on the following two Update & Upgrade jobs

- System update(Operating System and Running Environment) 
- MySQL upgrade 

## System Update

Run an update command to complete the system update:

``` shell
#For Ubuntu&Debian
apt update && apt upgrade -y

#For Centos&Redhat
yum update -y
```
> This deployment package is pre-configured with a scheduled task for automatic updates. If you want to remove the automatic update, please delete the corresponding Cron

## MySQL Upgrade

### On Linux

The system update command can update MySQL patch also, e.g: 5.6.x to 5.6.y or 5.7.x to 5.7.y

There are large differences between database distribution versions, which cannot provide a secure upgrade solution

### On Windows

### On Windows

MySQL upgrade on Windows Server divided into two parts

1. Use Windows Update to upgrade Windows System
2. Dowload the lastest MySQL, stop the MySQL Services and replace the old files of MySQL