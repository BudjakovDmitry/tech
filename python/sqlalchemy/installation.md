# SQLAlchemy installation

## Supported platforms

SQLAlchemy supports following platforms:

* cPython 3.7 and higher;
* Python3 compatible versions of PyPy;

## Install via pip

```shell
pip install SQLAlchemy
```

This command will download the latest **released** version of SQLAlchemy from PyPi and
install it to your system. For most common platforms, a Python Wheel file will be
downloaded which provides native Cython / C extensions prebuilt.

In order to install latest **prerelease** version, pip requires that the `--pre` flag be
used.

```shell
pip install --pre SQLAlchemy
```

## Installing manually from the source distribution

When not installing from `pip`, the source distribution may be installed using the
`setup.py` script.

```shell
python setup.py install
```

The source install is platform-agnostic and will install on any platform regardless of
whether Cython / C build tools are installed.

## Checking the installed SQLAlchemy version

```python
import sqlalchemy
sqlalchemy.__version__
# 2.0.0
```
