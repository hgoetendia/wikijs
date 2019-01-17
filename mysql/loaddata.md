<!-- TITLE: Load data -->

# Load CVS file into table


```mysql
mysql> LOAD DATA INFILE '/tmp/country.csv' INTO TABLE country FIELDS TERMINATED BY ',';
```
