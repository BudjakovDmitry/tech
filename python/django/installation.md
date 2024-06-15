# Install Django

You've got three options to install Django:

- Install an official release.
- Install a version of Django provided by your operating system distribution.
- Install the latest development version.

## Install with pip

```shell
# create virtual environment and activate it
python3 -m venv env_name
source env_name/bin/activate

# install Django via pip
python -m pip install Django

# check the installation was successful
python -m django --version
```