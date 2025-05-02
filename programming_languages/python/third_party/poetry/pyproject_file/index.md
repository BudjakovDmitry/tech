# The pyproject.toml file

## The project section

The project section of the `pyproject.toml` file according to the specification of the
PyPA.

### name

The name of the package. Always required when the `project` section is specified.

This should be a valid name as defined by PEP 508.

```toml
name = "my-package"
```

## The `tool.poetry` section

### package-mode

Poetry can be operated in two different modes. The default mode is the __package mode__,
which is the right mode if you want to package your project into an sdist or a wheel and
perhaps publish it to a package index. In this mode, some metadata such as `name` and
`version`, which are required for packaging, are mandatory. Further, the project itself
will be installed in editable mode when running `poetry install`.

If you want to use Poetry only for dependency management but not for packaging, you can
use the __non-package__ mode:

```toml
[tool.poetry]
package-mode = false
```

In this mode, metadata such as `name` and `version` are optional. Therefore, it is not
possible to build a distribution or publish the project to a package index. Further,
when running `poetry install`, Poetry does not try to install the project itself, but
only its dependencies (same as `poetry install --no-root`).

### packages

A list of packages and modules to include in the final distribution.

If your project structure differs from the standard one supported by poetry, you can
specify the packages you want to include in the final distribution.

```toml
[tool.poetry]
# ...
packages = [
    { include = "my_package" },
    { include = "extra_package/**/*.py" },
]
```

If your package is stored inside a “lib” directory, you must specify it:

```toml
[tool.poetry]
# ...
packages = [
    { include = "my_package", from = "lib" },
]
```

The `to` parameter is designed to specify the relative destination path where the
package will be located upon installation. This allows for greater control over the
organization of packages within your project’s structure.

```toml
[tool.poetry]
# ...
packages = [
    { include = "my_package", from = "lib", to = "target_package" },
]
```

If you want to restrict a package to a specific build format you can specify it by using
`format`:

```toml
[tool.poetry]
# ...
packages = [
    { include = "my_package" },
    { include = "my_other_package", format = "sdist" },
]
```

From now on, only the `sdist` build archive will include the `my_other_package` package.
