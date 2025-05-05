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

## Available variables

### virtualenvs.create

__Type__: `boolean`

__Default__: `true`

__Environment variable__: `POETRY_VIRTUALENVS_CREATE`

Create a new virtual environment if one doesn’t already exist.

If set to `false`, Poetry will not create a new virtual environment. If it detects an
already enabled virtual environment or an existing one in `{cache-dir}/virtualenvs` or
`{project-dir}/.venv` it will install dependencies into them, otherwise it will install
dependencies into the systems python environment.

If Poetry detects it’s running within an activated virtual environment, it will never
create a new virtual environment, regardless of the value set for `virtualenvs.create`.

Be aware that installing dependencies into the system environment likely upgrade or
uninstall existing packages and thus break other applications. Installing additional
Python packages after installing the project might break the Poetry project in return.
This is why it is recommended to always create a virtual environment. This is also true
in Docker containers, as they might contain additional Python packages as well.
