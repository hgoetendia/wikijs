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
