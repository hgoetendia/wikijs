<!-- TITLE: Load data -->

# Load CVS file into table: LOAD DATA INFILE

## If csv file columns match with table fields

```mysql
mysql> LOAD DATA INFILE '/tmp/country.csv' INTO TABLE country FIELDS TERMINATED BY ',';
```

## Into specific table fields

```mysql
mysql> LOAD DATA INFILE '/tmp/country.csv' INTO TABLE country FIELDS TERMINATED BY ',' (field_1, field_2, field_3);
```

