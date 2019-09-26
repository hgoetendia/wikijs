<!-- TITLE: Create, grantuser, revoke -->


# Create an user


```text
mysq [localhost] {root} ((none)) > CREATE USER 'myuser'@'localhost' IDENTIFIED BY 'mypass';
Query OK, 0 rows affected (0.00 sec)

mysql [localhost] {root} ((none)) > flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql [localhost] {root} ((none)) > 
```


# Create and grant all privileges to a user identified by pass


```sql
mysql> grant all on mydb.* to 'myuser'@'%' identified by 'mypass';
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> flush privileges;
```

# Create and grant read privileges to user


```sql
mysql> grant select on mydb.* to 'myuser'@'192.168.10.1' identified by '2eLhWL1advPBzXi4';
mysql> flush privileges;
```

# Revoke

```sql
mysql> REVOKE ALL PRIVILEGES ON *.* FROM 'myuser'@'%';
mysql> drop user myuser;
mysql> show grants for myuser;
ERROR 1141 (42000): There is no such grant defined for user 'myuser' on host '%'
 [localhost] {anUser} (MyDB) >
```