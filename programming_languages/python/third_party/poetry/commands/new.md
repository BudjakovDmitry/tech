# new

This command will create a new Poetry project. By default, a `src` layout is chosen.

```shell
poetry new my-awesome-project
```

will create a folder as follows:

```
my-awesome-project/
├── pyproject.toml
├── README.md
├── src
│    └── my_awesome_project
│        └── __init__.py
└── tests
    └── __init__.py
```

## Options

* `--name`: Set the resulting package name.

```shell
poetry new my-folder --name my-package
```

```
my-folder/
├── pyproject.toml
├── README.md
├── src
│   └── my-package
│       └── __init__.py
└── tests
    └── __init__.py
```

The `--name` option is smart enough to detect namespace packages and create the required
structure for you.

```shell
poetry new --name my.package my-package
```

```
my-package/
├── pyproject.toml
├── README.md
├── src
│   └── my
│       └── package
│           └── __init__.py
└── tests
    └── __init__.py

```

* `--flat`: Use the flat layout for the project.

```shell
poetry new --flat my-package
```

```
my-package/
├── pyproject.toml
├── README.md
├── my_package
│   └── __init__.py
└── tests
    └── __init__.py
```
