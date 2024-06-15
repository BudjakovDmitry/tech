# startproject

```shell
django-admin startproject name [diretory]
```

Creates a Django project directory structure for the given project name in the current
directory or the given destination.

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
