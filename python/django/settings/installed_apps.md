# INSTALLED_APPS

Default: `[]` (empty list).

A list of strings designating all applications that are enable in this Django
installation. Each string should be a dotted Python path to:

- an application configuration class (preferred), or;
- a package containing an application.

> Your code should never access `INSTALLED_APPS` directly. Use `django.apps.apps`
> instead.

Application names - the dotted Python path to the application package - must be unique.
There is no way to include the same application twice, short of duplicating its code
under another name.

Application labels - by default the final part of the name - must be unique too. For
example, you can't include both `django.contrib.auth` and `myproject.auth`. However,
you can relabel an application with a custom configuration that defines a different
label.

When several applications provide different versions of the same resource (template,
static file, management command, translation), the application listed first in
`INSTALLED_APPS` has precedence.
