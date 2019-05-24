<!-- TITLE: Create and grantuser -->

# Create and grant read privileges to user


```sql
mysql> grant select on mydb.* to 'myuser'@'192.168.10.1' identified by '2eLhWL1advPBzXi4';
mysql> flush privileges;
```