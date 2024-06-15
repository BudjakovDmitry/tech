# startproject

```shell
django-admin startproject name [diretory]
```

Creates a Django project directory structure for the given project name in the current
directory or the given destination.

>You'll need to avoid naming projects after built-in Python or Django components. You
> should avoid using names like *django* (conflict with Django itself) or *test*
> (conflicts with a build-in Python package).

By default, the new directory contains *manage.py* and a project package (containing a
*settings.py* and other files).

If only project name is given, both the project directory and project package will be
named *\<name\>* and the project directory will be created in the current working
directory.

If the optional destination is provided, Django will use that existing directory as the
project directory, and create *manage.py* and the project package within it.

```shell
django-admin startproject myproject /home/johndoe/code/myproject_repo
```

Startproject command will create directory tree:

```
project_name/
    manage.py
    project_name/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
```

- The outer *project_name* root directory is a container for your project; you can
rename it to anything you like.
- The inner *project_name* directory is the actual Python package for your project. Its
name you will need to use to import anything inside it (e.g. `project_name.urls`).
- *project_name/settings.py* contains settings and configurations for this Django
project.
- *project_name/urls.py* - the urls declarations for this Django project.
- *project_name/asgi.py* - an entry-point for ASGI-compatible web servers.
- *project_name/wsgi.py* - an entry-point for WSGI-compatible web servers.
