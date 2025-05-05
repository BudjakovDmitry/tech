# Configuration

## Using environment variables

Sometimes, in particular when using Poetry with CI tools, it’s easier to use environment
variables and not have to execute configuration commands. Poetry supports this and any
setting can be set by using environment variables. The environment variables must be
prefixed by `POETRY_` and are comprised of the uppercase name of the setting and with
dots and dashes replaced by underscore, here is an example:

```shell
export POETRY_VIRTUALENVS_PATH=/path/to/virtualenvs/directory
```

This also works for secret settings, like credentials:

```shell
export POETRY_HTTP_BASIC_MY_REPOSITORY_PASSWORD=secret
```
