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
