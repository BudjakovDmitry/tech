# Options

## -h, --help

`-h`, `--help` show help message and exit

```shell
pylint --help
```

---

## --long-help

Show more verbose help.

```shell
pylint --long-help
```

---

`--help-msg HELP_MSG [HELP_MSG ...]` Display a help message for the given message id and
exit. The value may be a comma separated list of message ids.
`missing-module-docstring`

```shell
pylint --help-msg missing-module-docstring
pylint --help-msg missing-module-docstring, invalid-name
```

---

`--const-rgx='<regexp>'` Regular expression matching correct constant name.
Overrides const-naming-style. If left empty, constant name will be checked with the set
naming style. (default: None).

Of course, we don't have to specify regex on the command line all the time. That's what
a configuration file for.

```shell
pylint script.py --const-rgx='[a-z\_][a-z0-9\_]{2,30}$'
```

---

`pylint --generate-toml-config` Generate a sample configuration file according to the
current configuration. You can put other options before this one to get them in the
generated configuration. The config is in the `.toml` format. This can then be added
to your `pyproject.toml` file or any other `.toml` file pointed to the `--rcfile`
option.

```shell
pylint --generate-toml-config
```

---

`--py-version <py_version>`

It's possible to analyse code written for older or multiple interpreters by using the
`py-version` option and setting it to the oldest supported interpreter of your code. For
example, you can check that there are no `f-strings` in Python 3.5 code using Python 3.8
with an up-to-date pylint even if Python 3.5 is past end of life (EOL) and the version
of pylint you use is not compatible with it.

---

`--rcfile RCFILE` Specify a configuration file to load.

---

`--recursive <yn>` Discover python modules and packages in the file system subtree (
default: False).

Pylint will not import this package or module, but it does use Python internals to
locate them. You should pay attention to your `PYTHONPATH`, since it is a common error
to analyze an installed version of a module instead of the development version.

```shell
ptlint --recursive=y mydir
```

---

`--source-roots <path>[, <path>]` Add path to the list of the source roots. Supports
globbing patterns. The source root is an absolute path or a path relative to the current
working directory used to determine a package namespace for modules located under the
source root (default: ()).

---

## --version

Show program's version and exit

```shell
pylint --version
```
