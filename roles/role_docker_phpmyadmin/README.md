Ansible Role: Docker_phpMyAdmin
=========

在CentOS或者Ubuntu服务器上安装和配置Docker版phpMyAdmin

Requirements
------------

无特殊要求,此 role 需要 root 用户权限,可以在playbook全局加入 `become: yes`,或者如下调用 role:

```
- hosts: all
  roles:
    - role: role_phpmyadmin
      become: yes
```

Role Variables
--------------

下面列出了可用变量和默认值(请参见"defaults/main.yml"):

```
mysql_root_password: 123456
```



Dependencies
------------

None

Example Playbook
----------------

```
- hosts: all
  become: yes
  vars_files:
    - vars/main.yml
  roles:
    - { role: role_phpmyadmin }
```

`vars/main.yml` :
```
mysql_root_password: ABCDEFG

```

License
-------

BSD

