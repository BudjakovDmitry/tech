# Examples

## load dotenv

```python
from dotenv import load_dotenv

load_dotenv()
```

By default, `load_dotenv` doesn't override existing environment variables and looks for
a `.env` file in same directory as python script or searches for it incrementally higher
up.

To configure the development environment, add a `.env` in the root directory of your
project.

The syntax of `.env` files supported by python-dotenv is similar to that of Bash:

```shell
# development settings
DOMAIN=example.org
ADMIN_EMAIL=admin@{DOMAIN}
ROOT_URL=${DOMAIN}/app
```

If you use variables in values, ensure they are surrounded with `{` and `}`. like
`${DOMAIN}`, as bare variables such as `$DOMAIN` are not expanded.

## load configuration without altering the environment

The function `dotenv_values` works more or less the same way as `load_dotenv`, except it
doesn't touch the environment, it just returns a `dict` with the values parsed from the
`.env` file.

```python
from dotenv import dotenv_values

config = dotenv_values(".env")
# config = {"USER": "foo", "EMAIL": "foo@example.org"}
```

Advanced configuration management:

```python
import os
from dotenv import dotenv_values

config = {
    **dotenv_values(".env.shared"),  # load shared development variables
    **dotenv_values(".env.secret"),  # load sensitive variables
    **os.environ,  # override loaded values with environment variables
}
```
