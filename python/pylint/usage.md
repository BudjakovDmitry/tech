# Usage

## Libraries support

Pylint supports Python standard library out of the box. Third party libraries are not
always supported, so a plugin might be needed. A good place to start is `PyPI` which
often returns a plugin by searching for `pylint <library>`.
[pylint-pydantic](https://pypi.org/project/pylint-pydantic),
[pylint-django](https://github.com/pylint-dev/pylint-django) and
[pylint-sonarjson](https://github.com/omegacen/pylint-sonarjson) are examples of such
plugins.

## The killer feature

Pylint is interring the actual values of nodes using its internal code representation
(astroid). If your code is `import logging as argparse`, Pylint can check and know that
`argparse.error(...)` is in fact a logging call and not an argparse call. This makes
pylint slower, but it also lets pylint find more issues if code is not fully typed.

## On module packages or directories

Pylint is meant to be called from the command line. The usage is:

```shell
pylint [options] modules_or_packages
```

By default, the `pylint` command only accepts a list of python modules and packages.
Specifying a directory that is not an explicit package (with `__init__.py`) results in
an error.

```shell
pylint mypackage
pylint --recursive=y mydir
```

## On files

It is also possible to analyze Python files with a few restrictions. As a convenience,
you can give it a file name if it's possible to guess a module name from the file's
path using the python path.

`pylint mymodule.py` should always work since the current working directory is
automatically added on the top of the python path.

`pylint directory/mymodule.py` will work if: `directory` is a python package (has an
`__init__.py` file), an implicit namespace package or if `directory` is in the python
path.

## With implicit namespace packages

If the analyzed sources use implicit namespace packages, the source root(s) should be
specified using the `--source-roots` option. Otherwise, the package names are detected
incorrectly, since implicit namespace packages don't contain an `__init__.py`

## Globbing support

It is possible to specify both directories and files using globbing patterns:

```shell
pylint [options] packages/*/src
```
