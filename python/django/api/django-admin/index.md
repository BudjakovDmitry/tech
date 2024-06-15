# django-admin and manage.py

`django-admin` is Django's command-line utility for administrative tasks.

In addition, *manage.py* is automatically created in each Django project. It does the
same thing as `django-admin` but also sets the `DJANGO_SETTINGS_MODULE` environment
variable so that it points to your project's *settings.py* file.

The `django-admin` script should be on your system path if you installed Django via
*pip*.

If ypu need to switch between multiple Django settings files, use `django-admin` with
`DJANGO_SETTINGS_MODULE` or the `--settings` command line option.

The command-line examples through this document use `django-admin` but any example can
use `dhango-admin` or *manage.py* or `python -m django` just as well.

```shell
django-admin <command> [options]
manage.py <command> [options]
python -m django <command> [options]
```

## Available commands

- [startproject](commands/startproject.md)

## Getting runtime help

```shell
# display usage information and a list of a commands provided by each application
django-admin help

# display a list of available commands
django-admin help --commands

# display a description of a given command and a list of available options
django-admin help <command>
```

## App names

Many commands take a list of "app names". An "app name" is the basename of the package
containing your models. For example, if your `INSTALLED_APPS` contains a string
`"mysite.blog"`, the app name is "blog".

## Determining version

Display current Django version.

```shell
django-admin version
```

## Display debug output

Use `--verbosity` where it is supported, to specify the amount of notification and debug
information the `django-admin` prints to the console.
