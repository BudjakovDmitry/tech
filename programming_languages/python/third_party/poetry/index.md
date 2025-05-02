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
