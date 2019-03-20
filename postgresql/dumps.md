<!-- TITLE: Dumps -->
<!-- SUBTITLE: A quick summary of Dumps -->

# Dumping schema only of a whole database


```sh
pg_dump -s database_name > db.sql
```

# Dump schema of specific table


```sh
pg_dump -s database_name -t table_name > db.sql 
```

# Restore 


```sh
psql -d database_name -h localhost -U postgres < path/db.sql
```
