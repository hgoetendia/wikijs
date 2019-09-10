<!-- TITLE: Install -->
<!-- SUBTITLE: A quick summary of Install -->

# MySQL Install in UBUNTU


```sh
$ sudo apt-get install mysql-server
```


# Configuring

# mysql

```sh
# mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 7
Server version: 5.7.26-0ubuntu0.19.04.1 (Ubuntu)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

```


# MySQL in Slackware


```text
# slackpkg install mysql

# ls -l /etc/my*

-rw-r--r-- 1 root root 4780 2010-05-05 15:53 /etc/my-huge.cnf
-rw-r--r-- 1 root root 4754 2010-05-05 15:53 /etc/my-large.cnf
-rw-r--r-- 1 root root 4765 2010-05-05 15:53 /etc/my-medium.cnf
-rw-r--r-- 1 root root 2403 2010-05-05 15:53 /etc/my-small.cnf

# cp /etc/my-small.cnf /etc/my.cnf

# mysql_install_db --user=mysql

# chmod 755 /etc/rc.d/rc.mysqld
```

Enable networking if needed 
Networking is disabled by default to improve security. If you want to allow network connections, comment out this line in /etc/rc.d/rc.mysqld:
rc.mysqld `#SKIP="--skip-networking"`

```text
# /etc/rc.d/rc.mysqld start

# /usr/bin/mysqladmin -u root password 'your-pass-here'

# mysql_secure_installation

```

