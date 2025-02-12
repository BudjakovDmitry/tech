# Running Gunicorn

You can run Gunicorn by using commands or integrate with popular frameworks.

## Gunicorn command

After installing Gunicorn you will have access to the command line script `gunicorn`.
Basic usage

```shell
gunicorn [OPTIONS] [WSGI_APP]
```

Where `WSGI_APP` is of the pattern `$(MODULE_NAME):$(VARIABLE_NAME)`. The module name
can be a full dotted path. The variable name refers to a WSGI callable that should be
found in the specified module.

`WSGI_APP` is optional if it is defined in a config file.

Example:

```python
def app(environ, start_response):
    """Simplest possible application object"""
    data = b"Hello, World!\n"
    status = "200 OK"
    response_headers = [
        ("Content-type", "text/plain"),
        ("Content-Length", str(len(data)))
    ]
    start_response(status, response_headers)
    return iter([data])
```

You can run the app with the following command:

```shell
gunicorn --workers=2 test:app
```

The variable name can be a function call. In that case the name will be imported from
the module, then called to get the application object. This is commonly referred to as
the "application factory" pattern.

```python
def create_app():
    app = FrameworkApp()
    ...
    return app
```

```shell
gunicorn --workers=2 'test:create_app()'
```

Positional and keywords arguments can also be passed, but it is recommended to load
configuration from environment variables rather than the command line.

### Options

- `-c CONFIG`, `--config=CONFIG` - specify a config file in the form `$(PATH)`,
`file:$(PATH)`, or `python:$(MODULE_NAME)`.
