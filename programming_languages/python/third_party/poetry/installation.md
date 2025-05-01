# Installation

## With the official installer

### 1. Install

The installer script is available directly at https://install.python-poetry.org/, and is
developed in
[its own repository](https://github.com/python-poetry/install.python-poetry.org). The
script can be executed directly or downloaded and then executed from disk.

```shell
curl -sSL https://install.python-poetry.org | python3 -
```

### 2. Install (advanced
)
By default, Poetry is installed into a platform and user-specific directory:

* `~/.local/share/pypoetry` on Linux/Unix

If you wish to change this, you may define the `$POETRY_HOME` environment variable:

```shell
curl -sSL https://install.python-poetry.org | POETRY_HOME=/etc/poetry python3 -
```

If you want to install prerelease versions, you can do so by passing the `--preview`
option to the installation script or by using the `$POETRY_PREVIEW` environment
variable:

```shell
curl -sSL https://install.python-poetry.org | python3 - --preview
curl -sSL https://install.python-poetry.org | POETRY_PREVIEW=1 python3 -
```

Similarly, if you want to install a specific version, you can use `--version` option or
the `$POETRY_VERSION` environment variable:

```shell
curl -sSL https://install.python-poetry.org | python3 - --version 1.8.4
curl -sSL https://install.python-poetry.org | POETRY_VERSION=1.8.4 python3 -
```

You can also install Poetry from a git repository by using the `--git` option:

```shell
curl -sSL https://install.python-poetry.org | python3 - --git https://github.com/python-poetry/poetry.git@main
```

### 3. Add Poetry to your PATH

The installer creates a `poetry` wrapper in a well-known, platform-specific directory:

* `$HOME/.local/bin` on Unix.

If this directory is not present in your `$PATH`, you can add it in order to invoke
Poetry as `poetry`.

Alternatively, the full path to the poetry binary can always be used:

* `~/.local/share/pypoetry/venv/bin/poetry` on Linux/Unix.

### 4. Use Poetry

Once Poetry is installed and in your `$PATH`, you can execute the following:

```shell
poetry --version
```

### 5. Update Poetry

Poetry is able to update itself when installed using the official installer.

```shell
poetry self update
```

If you want to install pre-release versions, you can use the --preview option.

```shell
poetry self update --preview
```

And finally, if you want to install a specific version, you can pass it as an argument
to `self update`.

```shell
poetry self update 1.8.4
```

### 6. Uninstall Poetry

You can completely remove Poetry from your system by running the installer again with
the `--uninstall` option or by setting the `POETRY_UNINSTALL` environment variable
before executing the installer.

```shell
curl -sSL https://install.python-poetry.org | python3 - --uninstall
curl -sSL https://install.python-poetry.org | POETRY_UNINSTALL=1 python3 -
```
