<!-- TITLE: Funcprocs -->
<!-- SUBTITLE: A quick summary of Funcprocs -->

# Show procedures


```text
MariaDB [accounts]> SHOW PROCEDURE STATUS;
+----------+-------------------------------------+-----------+-----------------------+---------------------+---------------------+---------------+---------+----------------------+----------------------+--------------------+
| Db       | Name                                | Type      | Definer               | Modified            | Created             | Security_type | Comment | character_set_client | collation_connection | Database Collation |
+----------+-------------------------------------+-----------+-----------------------+---------------------+---------------------+---------------+---------+----------------------+----------------------+--------------------+
| mydatab  | UPDATE_SUMMARY_FINISHED_STATUS_PROC | PROCEDURE |    myuser@localhost   | 2018-07-09 16:51:27 | 2018-07-09 16:51:27 | DEFINER       |         | utf8                 | utf8_general_ci      | latin1_swedish_ci  |
| test     | AddGeometryColumn                   | PROCEDURE | @                     | 2015-11-23 13:58:59 | 2015-11-23 13:58:59 | DEFINER       |         | latin1               | latin1_swedish_ci    | latin1_swedish_ci  |
| test     | DropGeometryColumn                  | PROCEDURE | @                     | 2015-11-23 13:58:59 | 2015-11-23 13:58:59 | DEFINER       |         | latin1               | latin1_swedish_ci    | latin1_swedish_ci  |
+----------+-------------------------------------+-----------+-----------------------+---------------------+---------------------+---------------+---------+----------------------+----------------------+--------------------+
6 rows in set (0.00 sec)
```

# Show functions

```text

MariaDB [accounts]> SHOW FUNCTION STATUS;
Empty set (0.00 sec)

MariaDB [accounts]> 
```

As mysql root user


```text
MariaDB [accounts]> SHOW CREATE FUNCTION myfunc;

```
