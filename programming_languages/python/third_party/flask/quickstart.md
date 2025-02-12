# Quickstart

A minimal Flask application:

```python
# hello.py
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "Hello, World!"
```

`app = Flask(__name__)` here we create our WSGI application. The first argument is the
name of application's module or package. `__name__` is a convenient shortcut for this
that is appropriate for most cases. This is needed so that Flask knows where to look for
resources such as templates and static files.

To run the application, use the `flask` command or `python -m flask`. You need to tell
the Flask where your application is with the `--app` option.

```shell
flask --app hello run 
```
