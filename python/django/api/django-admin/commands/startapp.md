# startapp

```shell
django-admin startapp name [directory]
```

Creates a Django app directory structure for the given app name in the current directory
or the given destination.

By default, the new directory contains a *models.py* file and other app template files.
If only the app name is given, the app directory will be created in the current working
directory.

If the optional destination is provided, Django will use that existing directory rather
than creating a new one. You can use `.` to denote the current working directory.

```shell
django-admin startapp myapp /home/johndoe/code/myapp
```
