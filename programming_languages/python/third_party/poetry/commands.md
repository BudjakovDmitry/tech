# Commands

## init

This command will help you create a `pyproject.toml` file interactively by prompting you
to provide basic information about your package.

It will interactively ask you to fill in the fields, while using some smart defaults.

```shell
poetry init
```

### Options

* `--name`: Name of the package.
* `--description`: Description of the package.
* `--author`: Author of the package.
* `--python` Compatible Python versions.
* `--dependency`: Package to require with a version constraint. Should be in format
`foo:1.0.0`.
* `--dev-dependency`: Development requirements, see `--dependency`.
