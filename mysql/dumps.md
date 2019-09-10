<!-- TITLE: MySQL/Dumps -->

# Dumping a table
```sh
mysqldump -umyuser -p -hmyhost mydatabase mytable >  mytable_dump.sql
```

# Dump with master data to sync
```sh
mysqldump --all-databases --master-data | gzip -1 > /root/all.sql.gz
```

Tests

```sh
mysqldump -u root -p --databases database_name_a database_name_b > databases_a_b.sql
```

# Dump only schema
```sh
mysqldump --no-data -u someuser -p mydatabase
```

# Dump including, triggers, functions

```text
mysqldump -uroot -p  MyDB --routines > MyDB.sql
```

# Dump certain tables

```text
mysqldump -uroot -p mydb t1 t2 t3 > mydb_tables.sql

```

# Query to CSV

```mysql
mysql> SELECT order_id,product_name,qty
FROM orders
WHERE foo = 'bar'
INTO OUTFILE '/tmp/orders.csv'
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\n';
```
