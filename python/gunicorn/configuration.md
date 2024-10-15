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
