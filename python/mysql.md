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

## Fetch rows
## All

```python
row = cursor.fetchall()
print row[0]["key"]
```

in loop


```python
for row in cursor.fetchall():
    print("Name: %s" % row['can_name'])
```


## One

```python
row = cursor.fetchone()
print row["key"]
```


## Pool of connections

pip install pymysql-pool




```python
import pymysqlpool

config={'host':'bdk.com', 'user':'albus', 'password':'XXXX', 'database':'acts', 'cursorclass':pymysql.cursors.DictCursor}

pool1 = pymysqlpool.ConnectionPool(size=5, name='pool1', **config)

connection = pool1.get_connection(timeout=0, retry_num=0)

 try:

        with connection.cursor() as cursor:
            # Read a single record
            sql = ("SELECT p.id_process, p.process_type, p.tag, p.description, "
                   "p.status, pp.parameter, pp.value "
                   "FROM process p, process_param pp "
                   "WHERE p.id_process = pp.id_process AND "
                   "p.tag=%s AND p.process_type=%s")
            cursor.execute(sql, ('GRANJA1','KRAKEN',))

            for row in cursor.fetchall():
                
                ID_PROCESS = row['id_process']
                PROCESS_TYPE  = row['process_type']

                if row['parameter'] == "ID_COUNTRY":
                    ID_COUNTRY = row['value']

                if row['parameter'] == "WAY":
                    WAY = row['value']

                if row['parameter'] == "SERVER_PORT":
                    SERVER_PORT = row['value']

                if row['parameter'] == "MAX_MESSAGES":
                    MAX_MESSAGES = row['value']
                        
            print(ID_COUNTRY + ":" + WAY + ":" + SERVER_PORT + ":" + MAX_MESSAGES)
                
            
    finally:
        connection.close()

```
