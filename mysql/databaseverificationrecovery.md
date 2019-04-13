<!-- TITLE: Database verification recovery -->
<!-- SUBTITLE: A quick summary of Databaseverificationrecovery -->


# Avoid database verification recovery

* Start database withouth innoDB verification/recovery
Add in `/etc/my.cnf.d/server.cnf` the line

```text
innodb_force_recovery = 1
```
