# add

The `add` command adds required packages to your `pyproject.toml` and installs them.

If you do not specify a version constraint, poetry will choose a suitable one based on
the available package versions.

```shell
poetry add requests pendulum
```

You can also specify a constraint when adding a package:

```shell
# Allow >=2.0.5, <3.0.0 versions
poetry add pendulum@^2.0.5

# Allow >=2.0.5, <2.1.0 versions
poetry add pendulum@~2.0.5

# Allow >=2.0.5 versions, without upper bound
poetry add "pendulum>=2.0.5"

# Allow only 2.0.5 version
poetry add pendulum==2.0.5
```

You can also add a local directory or file:

```shell
poetry add ./my-package/
poetry add ../my-package/dist/my-package-0.1.0.tar.gz
poetry add ../my-package/dist/my_package-0.1.0.whl
```
