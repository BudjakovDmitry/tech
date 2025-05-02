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
