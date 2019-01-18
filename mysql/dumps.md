<!-- TITLE: MySQL/Dumps -->

# Dumping a table

```sh
mysqldump -umyuser -p -hmyhost mydatabase mytable >  mytable_dump.sql
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
