# run

Executes the given command inside the project’s virtualenv.

```shell
poetry run python -V
```

It can also execute one of the scripts defined in `pyproject.toml`.

If you have a script defined like this:

```toml
[project]
# ...
[project.scripts]
my-script = "my_module:main"
```

You can execute it like so:

```shell
poetry run my-script
```

Note that this command has no option.
