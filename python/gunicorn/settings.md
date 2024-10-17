# Settings

Some settings are only able to be set from a configuration file.

## Debugging

### reload

Command line: `--reload`

Default: `False`

Restart workers when code changes.

This setting is intended for development.

### check_config

Command line: `--check-config`

Default: `False`

Check the configuration and exit. The result status is 0 if the configuration is
correct, and 1 if the configuration is incorrect.

### print_config

Command line: `--print-config`

Default: `False`

Print the configuration settings as fully resolved.

## Logging

### accesslog

Command line: `--access-logfile FILE`

Default: `None`

The Access log file to write to. `-` means log to stdout.

### errorlog

Command line: `--error-logfile FILE` or `--log-file FILE`

Default: `-`. Using `-` for FILE makes gunicorn log to stderr.

The error log file to write to.
