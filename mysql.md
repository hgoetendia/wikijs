<!-- TITLE: Mysql -->

* [Days of current month](/mysql/daysofmonth)

* [Dumps](/mysql/dumps)

* [Jump slave errors](mysql/jumpslaveerrors)

* [Disable replication for the current session](mysql/disablereplicationforsession)

* [Triggers](mysql/triggers)

* [Functions and procedures](mysql/funcsprocs)

* Rename table
```mysql
MySQL [database]> RENAME TABLE tb1 TO tb2;
```
```mysql
MySQL [database]> RENAME TABLE tb1 TO tb2, tb3 TO tb4;
```


# Tricks

* [Load data](mysql/loaddata)

* Start database withouth innoDB verification/recovery
Add in `/etc/my.cnf.d/server.cnf` the line

```text
innodb_force_recovery = 1
```
