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


# Example
Requerimients:

```sh
pip  install  mysql-connector-python
```

Example


```python

import mysql.connector.pooling
import mysql.connector
import warnings
import logging
logging.basicConfig(format='%(asctime)s %(message)s', level=logging.DEBUG)

config_pool={'host':'127.0.0.1',
             'user':'myuser',
             'password':'secret',
             'database':'mydb',
             'autocommit' : True,
             'connect_timeout' : 30             
             }


while True:
    try:
        logging.info("Conectando a la BD");
        cnxpool = mysql.connector.pooling.MySQLConnectionPool(pool_name='whatssapp_dbpool', pool_size=5, **config_pool)
        logging.info("Conectado")
        break
    except Exception as e:
        logging.error(str(e))
        logging.error("No se puede conectar ")
        logging.info("Intentando nuevamente en 5 segs")
        time.sleep(5);
				
def get_numbers():

    connection = cnxpool.get_connection()

    rows = []

    try:
        connection.ping(True)
        cursor = connection.cursor(dictionary=True)
        sql = ("SELECT msisdn FROM numbers WHERE status='ENABLED' ORDER BY RAND()")
        cursor.execute(sql)

        rows = cursor.fetchall()

        cursor.close()
    except Exception as e:
        logging.error(str(e))
    finally:
        connection.close()

    return rows

```

