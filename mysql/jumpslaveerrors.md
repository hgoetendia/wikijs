<!-- TITLE: Mysql/Jump slave error -->
<!-- SUBTITLE: A quick summary of Jumpslaveerrors -->

# Jump replication slave error 
Repair MySQL Replication

Check
```text
mysql> SHOW SLAVE STATUS \G
*************************** 1. row ***************************
             Slave_IO_State: Waiting for master to send event
                Master_Host: 1.2.3.4
                Master_User: slave_user
                Master_Port: 3306
              Connect_Retry: 60
            Master_Log_File: mysql-bin.001079
        Read_Master_Log_Pos: 269214454
             Relay_Log_File: slave-relay.000130
              Relay_Log_Pos: 100125935
      Relay_Master_Log_File: mysql-bin.001079
           Slave_IO_Running: Yes
          Slave_SQL_Running: No
            Replicate_Do_DB: mydb
        Replicate_Ignore_DB:
         Replicate_Do_Table:
     Replicate_Ignore_Table:
    Replicate_Wild_Do_Table:
Replicate_Wild_Ignore_Table:
                 Last_Errno: 1146
                 Last_Error: Error 'Table 'mydb.taggregate_temp_1212047760' doesn't exist' on query. Default database: 'mydb'. 
Query: 'UPDATE thread AS thread,taggregate_temp_1212047760 AS aggregate
        SET thread.views = thread.views + aggregate.views
        WHERE thread.threadid = aggregate.threadid'
               Skip_Counter: 0
        Exec_Master_Log_Pos: 203015142
            Relay_Log_Space: 166325247
            Until_Condition: None
             Until_Log_File:
              Until_Log_Pos: 0
         Master_SSL_Allowed: No
         Master_SSL_CA_File:
         Master_SSL_CA_Path:
            Master_SSL_Cert:
          Master_SSL_Cipher:
             Master_SSL_Key:
      Seconds_Behind_Master: NULL
1 row in set (0.00 sec)
```

Stop the slave
```text
mysql> STOP SLAVE;
```

Jump the error
```text
mysql> SET GLOBAL SQL_SLAVE_SKIP_COUNTER = 1;
```

Start the slave
```text
mysql> START SLAVE;
```

Check again
```text
mysql> SHOW SLAVE STATUS \G

*************************** 1. row ***************************
             Slave_IO_State: Waiting for master to send event
                Master_Host: 1.2.3.4
                Master_User: slave_user
                Master_Port: 3306
              Connect_Retry: 60
            Master_Log_File: mysql-bin.001079
        Read_Master_Log_Pos: 447560366
             Relay_Log_File: slave-relay.000130
              Relay_Log_Pos: 225644062
      Relay_Master_Log_File: mysql-bin.001079
           Slave_IO_Running: Yes
          Slave_SQL_Running: Yes
            Replicate_Do_DB: mydb
        Replicate_Ignore_DB:
         Replicate_Do_Table:
     Replicate_Ignore_Table:
    Replicate_Wild_Do_Table:
Replicate_Wild_Ignore_Table:
                 Last_Errno: 0
                 Last_Error:
               Skip_Counter: 0
        Exec_Master_Log_Pos: 447560366
            Relay_Log_Space: 225644062
            Until_Condition: None
             Until_Log_File:
              Until_Log_Pos: 0
         Master_SSL_Allowed: No
         Master_SSL_CA_File:
         Master_SSL_CA_Path:
            Master_SSL_Cert:
          Master_SSL_Cipher:
             Master_SSL_Key:
      Seconds_Behind_Master: 0
1 row in set (0.00 sec)

mysql>
```

Optional check the `/var/log/syslog` file.

All in a single line:
```text
STOP SLAVE; SET GLOBAL SQL_SLAVE_SKIP_COUNTER = 1; START SLAVE; SHOW SLAVE STATUS \G
```
