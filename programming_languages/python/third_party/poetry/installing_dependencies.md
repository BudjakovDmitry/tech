# Installing dependencies

To install the defined dependencies for your project type:

```shell
poetry install
```

When you run this command, one of two things may happen:

## Installing without `poetry.lock`

If you have never run the command before and there is also no `poetry.lock` file
present, Poetry simply resolves all dependencies listed in your `pyproject.toml` file
and downloads the latest version of their files.

When Poetry has finished installing, it writes all the packages and their exact versions
that it downloaded to the `poetry.lock` file, locking the project to those specific
versions. You should commit the `poetry.lock` file to your project repo so that all
people working on the project are locked to the same versions of dependencies.

## Installing with `poetry.lock`

If there is already a `poetry.lock` file as well as a `pyproject.toml` file when you run
`poetry install`, it means either you ran the `install` command before, or someone else
on the project ran the `install` command and committed the `poetry.lock` file to the
project (which is good).

Either way, running `install` when a `poetry.lock` file is present resolves and installs
all dependencies that you listed in `pyproject.toml`, but Poetry uses the exact versions
listed in `poetry.lock` to ensure that the package versions are consistent for everyone
working on your project. As a result you will have all dependencies requested by your
`pyproject.toml` file, but they may not all be at the very latest available versions.
This is by design, it ensures that your project does not break because of unexpected
changes in dependencies.

## Committing your `poetry.lock` file to version control

### As an application developer

Application developers commit `poetry.lock` to get more reproducible builds.

Committing this file to VC is important because it will cause anyone who sets up the
project to use the exact same versions of the dependencies that you are using.
