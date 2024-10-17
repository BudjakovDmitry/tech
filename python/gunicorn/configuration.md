# Configuration

Gunicorn reads configuration information from five places.

Gunicorn first reads environment variables for some configuration settings.

Then reads configuration from framework specific configuration file. Currently, this
only affects Paster applications.

The third source of configuration information is an optional configuration file
`gunicorn.conf.py` searched in the current working directory or specified using a
command line argument. Anything specified in this configuration file will override any
frameworks specific settings.

The fourth place of configuration information are command line arguments stored in an
environment variable named `GUNICORN_CMD_ARGS`.

Lastly, the command line arguments used to invoke Gunicorn are the final place
considered for configuration settings. If an option is specified on the command line,
this is the value that will be used.

When a configuration file is specified in the command line arguments and in the
`GUNICORN_CMD_ARGS` environment variable, only the configuration file specified on the
command line is used.

Once again, in order of least to most authoritative:

1. Environment variables
2. Framework settings
3. Configuration file `gunicorn.conf.py`
4. `GUNICORN_CMD_ARGS`
5. Command line

To print your resolved configuration when using the command line or the configuration
file you can run the following command:

```shell
gunicorn --print-config APP_MODULE
```

To check your resolved configuration when using the command line or the configuration
file you can run the following command:

```shell
gunicorn --check-config APP_MODULE
```

It also allows you to know if your application can be launched.

## Command line

If an option is specified on the command line, it overrides all other values that may
have been specified in the app specific settings, or in the optional configuration file.
Not all Gunicorn settings are available to be set from the command line. To see the full
list of command line settings type:

```shell
gunicorn -h
```

There is also a `--version` flag available that isn't mentioned in the list of settings.

## GUNICORN_CMD_ARGS

All available command line arguments can be used.

```shell
GUNICORN_CMD_ARGS="--bind=127.0.0.1 --workers=3"
```
