<!-- TITLE: Mysql -->
<!-- SUBTITLE: A quick summary of Mysql -->

# Options for using Python 3 with mysql:
There are currently a few options for using Python 3 with mysql:

## mysql-connector-python
https://pypi.python.org/pypi/mysql-connector-python

Officially supported by Oracle
Pure python
A little slow
Not compatible with MySQLdb

## pymysql
https://pypi.python.org/pypi/pymysql

Pure python
Faster than mysql-connector
Almost completely compatible with MySQLdb, after calling pymysql.install_as_MySQLdb()

## cymysql
https://pypi.python.org/pypi/cymysql

fork of pymysql with optional C speedups

## mysqlclient
https://pypi.python.org/pypi/mysqlclient
Django's recommended library.
Friendly fork of the original MySQLdb, hopes to merge back some day
The fastest implementation, as it is C based.
The most compatible with MySQLdb, as it is a fork
Debian and Ubuntu use it to provide both python-mysqldb andpython3-mysqldb packages.

# pymysql

## Instalation


```sh
python3 -m pip install PyMySQL
```

To use “sha256_password” or “caching_sha2_password” for authenticate, you need to install additional dependency:

```sh
$ python3 -m pip install PyMySQL[rsa]
```


## Example


```python
import pymysql.cursors

# Connect to the database
connection = pymysql.connect(host='localhost',
                             user='user',
                             password='passwd',
                             db='db',
                             charset='utf8mb4',
                             cursorclass=pymysql.cursors.DictCursor)

try:
    with connection.cursor() as cursor:
        # Create a new record
        sql = "INSERT INTO `users` (`email`, `password`) VALUES (%s, %s)"
        cursor.execute(sql, ('webmaster@python.org', 'very-secret'))

    # connection is not autocommit by default. So you must commit to save
    # your changes.
    connection.commit()

    with connection.cursor() as cursor:
        # Read a single record
        sql = "SELECT `id`, `password` FROM `users` WHERE `email`=%s"
        cursor.execute(sql, ('webmaster@python.org',))
        result = cursor.fetchone()
        print(result)
finally:
    connection.close()
```


