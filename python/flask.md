<!-- TITLE: Flask -->
<!-- SUBTITLE: A quick summary of Flask -->

# Simple

Flask default port is 5000

```python
from flask import Flask, url_for
app = Flask(__name__)

@app.route('/')
def api_root():
    return 'Welcome'

@app.route('/articles')
def api_articles():
    return 'List of ' + url_for('api_articles')

@app.route('/articles/<articleid>')
def api_article(articleid):
    return 'You are reading ' + articleid

if __name__ == '__main__':
    app.run()
		#app.run(port=5000) #to run server in port 5000 
```
To test

curl http://127.0.0.1:5000/

The responses will be:

```text
GET /
Welcome

GET /articles
List of /articles

GET /articles/123
You are reading 123
```

Routes can use different converters in their definition,

`@app.route('/articles/<articleid>')`

Can be replaced by

`@app.route('/articles/<int:articleid>')`
`@app.route('/articles/<float:articleid>')`
`@app.route('/articles/<path:articleid>')`

The default is string which accepts any text without slashes.

# Get and parameters

```python

from flask import request

@app.route('/hello')
def api_hello():
    if 'name' in request.args:
        return 'Hello ' + request.args['name']
    else:
        return 'Hello John Doe'
```
Testing


```text
GET /hello
Hello John Doe

GET /hello?name=Luis
Hello Luis
```

# Request methods

Request Methods


```python

from flask import Flask, url_for, request

@app.route('/echo', methods = ['GET', 'POST', 'PATCH', 'PUT', 'DELETE'])
def api_echo():
    if request.method == 'GET':
        return "ECHO: GET\n"

    elif request.method == 'POST':
        return "ECHO: POST\n"

    elif request.method == 'PATCH':
        return "ECHO: PACTH\n"

    elif request.method == 'PUT':
        return "ECHO: PUT\n"

    elif request.method == 'DELETE':
        return "ECHO: DELETE"
```

To test

`curl -X PATCH http://127.0.0.1:5000/echo`

The replies to the different request methods will be:


```text
GET /echo
ECHO: GET

POST /ECHO
ECHO: POST
```

http://blog.luisrei.com/articles/flaskrest.html


# Shutdown flask server


```python
from flask import request

def shutdown_server():
    func = request.environ.get('werkzeug.server.shutdown')
    if func is None:
        raise RuntimeError('Not running with the Werkzeug Server')
    func()
Now you can shutdown the server by calling this function:

@app.route('/shutdown', methods=['POST'])
def shutdown():
    shutdown_server()
    return 'Server shutting down...'
```


# Example:


```python
import requests
import os
import time
import threading
import json
import pymysql.cursors
import pymysqlpool
import logging
import warnings

from datetime import datetime
from flask import Flask, url_for
from flask import request
from flask import Response

logger = None

def server(local_port):

    app = Flask(__name__)
    
    @app.route('/', methods = ['POST'])
    def api_root():

        if request.headers['Content-Type'] == 'application/json':
            data = request.get_json();
            try:                
                ret = "{'hola': 'mundo', 'python': 'flask' }"
                
                return Response(json.dumps(ret), mimetype='application/json')
            
            except Exception as e:
                resp =   {"hello": "world", "status": "FAIL" }
                return str(resp)
            
        return 'unknown'
    
    @app.route('/control', methods = ['POST'])
    def api_control():
        try:                
            ret = "{'hola': 'mundo', 'python': 'flask' }"
            
            return Response(json.dumps(ret), mimetype='application/json')
        
        except Exception as e:
            resp =   {"messageid": data['id'], "status": "FAIL" }
            return str(resp)
    
    @app.route('/control/<controlid>')
    def api_article(controlid):
        return 'You are reading ' + controlid

    app.run(port=local_port)

def init_logger(logFile):
    global logger
    logger = logging.getLogger('myapp')
    logger.setLevel(logging.DEBUG)
    # Log to file
    fh = logging.FileHandler(logFile)    
    fh.setLevel(logging.DEBUG)
    # Log to console
    ch = logging.StreamHandler()
    ch.setLevel(logging.ERROR)
    formatter = logging.Formatter('%(asctime)s [%(name)s][%(levelname)s]: %(message)s')
    fh.setFormatter(formatter)
    ch.setFormatter(formatter)
    # Add the handlers to the logger
    logger.addHandler(fh)
    logger.addHandler(ch)    
    logger.info('Logger was initialized')
    
def init():

    flag = False
    
    init_logger("example_application.log");
    
    with open('config.json') as config_file:
        conf = json.load(config_file)

    config_pool={'host'            : conf["DB_HOST"],
                 'user'            : conf["DB_USER"],
                 'password'        : conf["DB_PASSWORD"],
                 'database'        : conf["DATABASE"],
                 'autocommit'      : True,
                 'connect_timeout' : 30,
                 'read_timeout'    : 30,
                 'write_timeout'   : 30,
                 'cursorclass'     : pymysql.cursors.DictCursor}

    pymysqlpool.logger.setLevel('DEBUG')

    now = datetime.now()
    logger.debug(now)

    while True:
        try:
            logger.info("Trying to connect to BD");
            pool = pymysqlpool.ConnectionPool(size=conf["DB_POOL_SIZE"], name='pool', **config_pool)
            logger.info("Connected")
            break
        except Exception as e:
            logger.error(str(e))
            logger.error("Can't connect, trying in 5 secs")
            time.sleep(5);
    
    connection = pool.get_connection(timeout=conf["TIMEOUT_DB_CONN"], retry_num=conf["RETRY_DB_CONN"])

    try:

        with connection.cursor() as cursor:
            # Read a single record
            sql = ("SELECT %s AS id_process, %s AS process_type ")
            cursor.execute(sql, ('GRANJA1','GRANJA2',))

            #sql =("(SELECT * FROM foo WHERE %d=%d LIMIT %d)") % (1, 1, 1);

            for row in cursor.fetchall():                
                id_process   = row['id_process']
                process_type = row['process_type']

            logger.info("Data " + id_process + ":" +process_type)

            flag = True

    except Exception as e:
        logger.error(str(e))
        return
    finally:
        connection.close()

    if flag:
        server(conf["SERVER_PORT"])
            
if __name__ == '__main__':
    init()

```


Config file `config.json`


```json
{
  "DB_HOST"         : "127.0.0.1",
  "DB_USER"         : "mypowerfulluser",
  "DB_PASSWORD"     : "mysecretpassw",
  "DATABASE"        : "mydb",
  "TIMEOUT_DB_CONN" : 0,
  "RETRY_DB_CONN"   : 0,
  "DB_POOL_SIZE"    : 5,
  "SERVER_PORT"     : 5666
}
```


# Github

<script src="http://gist-it.appspot.com/https://github.com/dotnet/corefx/blob/master/src/System.ObjectModel/src/System/Windows/Input/ICommand.cs"></script>


test
