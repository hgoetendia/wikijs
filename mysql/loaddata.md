<!-- TITLE: Load data -->

# Load CVS file into table


```mysql
mysql> LOAD DATA INFILE '/tmp/country.csv' INTO TABLE country 
FIELDS TERMINATED BY ',' 
ENCLOSED BY '"'
LINES TERMINATED BY '\n'
IGNORE 1 ROWS
```
