# Poetry

Poetry is a tool for dependency management and packaging in Python.

* [Installation](installation.md)
* [The `pyproject.toml` file](pyproject_file/index.md)

## Project setup

Create a new project calling _demo_

```shell
poetry new demo
```

This will create the `demo` directory with the following content:

```
poetry-demo
├── pyproject.toml
├── README.md
├── src
│   └── demo
│       └── __init__.py
└── tests
    └── __init__.py
```

The `pyproject.toml` file is what is the most important here. This will orchestrate your
project and its dependencies. For now, it looks like this:

```
[project]
name = "demo"
version = "0.1.0"
description = ""
authors = [
    {name = "John Doe", email = "jd@python.in"}
]
readme = "README.md"
requires-python = ">=3.9"
dependencies = [
]

[build-system]
requires = ["poetry-core>=2.0.0,<3.0.0"]
build-backend = "poetry.core.masonry.api"
```

Poetry assumes your package contains a package with the same name as `project.name`
located in the root of your project. If this is not the case, populate
`tool.poetry.packages` to specify your packages and their locations.

## Installing pre-existing project

Instead of creating a new project, Poetry can be used to ‘initialise’ a pre-populated
directory. To interactively create a `pyproject.toml` file in directory
`pre-existing-project`:

```shell
cd pre-existing-project
poetry init
```

## Setting a Python version

Poetry will require you to explicitly specify what versions of Python you intend to
support, and its universal locking will guarantee that your project is installable (and
all dependencies claim support for) all supported Python versions. Again, it’s important
to remember that – unlike other dependencies – setting a Python version is merely
specifying which versions of Python you intend to support.

In next example we are allowing any version of Python 3 that is greater or equal than
`3.9.0`.

```toml
[project]
requires-python = ">=3.9"
```

When you run `poetry install`, you must have access to some version of a Python
interpreter that satisfies this constraint available on your system. Poetry will not
install a Python interpreter for you.

## Specifying dependencies

If you want to add dependencies to your project, you can specify them in the project
section.

```toml
[project]
# ...
dependencies = [
    "pendulum (>=2.1,<3.0)"
]
```

Poetry uses this information to search for the right set of files in package
“repositories” that you register in the `tool.poetry.source` section, or on PyPI by
default.

Also, instead of modifying the `pyproject.toml` file by hand, you can use the `add`
command.

```shell
$ poetry add pendulum
```

It will automatically find a suitable version constraint and install the package and
sub-dependencies.

## Virtual environment

By default, Poetry creates a virtual environment in `{cache-dir}/virtualenvs`. You can
change the `cache-dir` value by editing the Poetry configuration. Additionally, you can
use the `virtualenvs.in-project` configuration variable to create virtual environments
within your project directory.

Poetry will detect and respect an existing virtual environment that has been externally
activated. Simply activate a virtual environment using your preferred method or tooling,
before running any Poetry commands that expect to manipulate an environment.
