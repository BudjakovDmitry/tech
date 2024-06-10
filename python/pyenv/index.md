# pyenv

[GitHub repo](https://github.com/pyenv/pyenv)

pyenv lets you easily switch between multiple versions of Python.

At a high level, pyenv intercept Python commands using shim executables injected into
your `PATH`, determines which Python version has been specified by your application, and
passes your commands along to the correct Python installation.

## Understanding shims

pyenv works by inserting a directory of *shims* at the front of your `PATH`. 

```shell
$(pyenv root)/shims:/usr/local/bin:/usr/bin:/bin
```

Through a process called *rehashing*, pyenv maintains shims in that directory to match
every Python command across every installed version of Python - `python`, `pip` and so
on.

Shims are lightweight executables that simply pass your commands along to pyenv. So with
pyenv installed, when you run, say, `pip`, your operating system will do the following:

- Search your `PATH` for an exacutable file named `pip`.
- Find the pyenv shim named `pip` at the beginning of your `PATH`.
- Run the shim named `pip`, which in turn passes the command along to pyenv.

## Understanding Python version selection

When you execute a shim, pyenv determines which Python version to use by reading it from
the following sources, in this order:

1. The `PYENV_VERSION` environment variable (if specified). You can use the
`pyenv shell` command to set this environment variable in your current shell session.
2. The application-specific `.python-version` file in the current directory (if
present). You can modify the current directory's `.python-version` file with
`pyenv local` command.
3. The first `.python-version` file found (if any) by searching each parent directory,
until reaching the root of your filesystem.
4. The global `$(pyenv root)/version` file. You can modify this file using the
`pyenv global` command. If the global version is not present, pyenv assumes you want to
use "system" Python.

A special version name "`system`" means to use whatever Python is found on `PATH` after
the shims `PATH` entry (in other words, whatever would be run if Pyenv shims weren't on
`PATH`). So e.g. if you are on MacOS and have OS-bundled Python 3.8.9 and
Homebrew-installed Python 3.9.12 and 3.10.2 -- for Pyenv, this is still a single
"system" version, and whichever of those is first on PATH under the executable name you
specified will be run.

You can activate multiple versions at the same time. This allows for parallel usage of
Python2 and Python3, and is required with tools like `tox`. For example, to instruct
Pyenv to first use your system Python and Python3 (which are e.g. 2.7.9 and 3.4.2) but
also have Python 3.3.6, 3.2.1 and 2.5.2 available, you first `pyenv install` the
missing versions, then set `pyenv global system 3.3.6 3.2.1 2.5.2`. Then you'll be
able to invoke any of those versions with an appropriate `pythonX` or `pythonx.Y`
name. You can also specify multiple versions in a `.python-versions` file by hand,
separated by newlines. Lines starting with a `#` are ignored.

`pyenv which <command>` displays which real executable would be run when you invoke
`<command>` via shim.

```shell
pyenv which python3.9
# $(pyenv root)/versions/3.9.16/bin/python
```

Each Python version is installed into its own directory under `$(pyenv root)/versions`.
Version names are simply directories under `versions` directory.

Once pyenv has determined which version of Python your application has specified, it
passes the command along to the corresponding Python installation.

## Installation

### pyenv-installer

[pyenv-installer](https://github.com/pyenv/pyenv-installer)

Pyenv requires these libraries and tools to be installed (Debian/Ubuntu):

```shell
sudo apt install git
sudo apt install libedit-dev
sudo apt install libncurses5-dev6
```

Once prerequisites have been installed correctly:

```shell
curl https://pyenv.run | bash
```

`pyenv.run` redirects to the
[installation script](https://github.com/pyenv/pyenv-installer/blob/master/bin/pyenv-installer).

> If you wish to install a specific release of Pyenv rather than the latest head, set
> the `PYENV_GIT_TAG` environment variable (e.g. `export PYENV_GIT_TAG=v2.2.5`).

After installation set up your shell environment for Pyenv:

- Define environment variable `PYENV_ROOT` to point to the path where Pyenv will store
its data. `$HOME/.pyenv` is the default.
- Add the `pyenv` executable to your `PATH` if it's not already there.
- Run `eval "$(pyenv init -)"` to install `pyenv` into your shell as a shell function,
enable shims and autocompletion. You may run `evel "$(pyenv init --path)"` instead to
just enable shims, without shell integration.

For Bash:

- Add commands to `~/.bashrc`:

```shell
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
```

Then, if you have `~/.profile`, `~/.bash_profile` or `~/.bash_login`, add the commands
there as well. If you have none of these, add them to `~/.pofile`

```shell
# add to ~/.profile
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.profile
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.profile
echo 'eval "$(pyenv init -)"' >> ~/.profile
```

```shell
# add to ~/.bash_profile
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
```

Restart you shell for the `PATH` changes to take effect.

```shell
exec "$SHELL"
```

## Update

```shell
pyenv update
```

## Uninstall

`pyenv` is installed within `$PYENV_ROOT` (default `~/.pyenv`). To uninstall, just
remove it.

```shell
rm -fr ~/.pyenv
```

Then remove these three lines from `.bashrc`:

```shell
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv virtualenv-init -)"
```

and finally, restart your shell:

```shell
exec $SHELL
```

## Install Python build dependencies

Sometimes Python compilation fails because of unmet system dependencies, or compilation
succeed but the new Python exhibits weird failures at runtime.

Debian/Ubuntu/Mint

```shell
sudo apt update; sudo apt install build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev curl git \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

If you are going build PyPy from source or install other Python flavors that require
CLang, also install `llvm`.

## Commands

[Documentation](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md)

### global

Sets the global version of Python to be used in all shells by writing the version name
to the `~/.pyenv/version` file. This version can be overridden by an
application-specific `.python-version` file, or by setting the `PYENV_VERSION`
environment variable.

```shell
pyenv global 3.11.5
```

The special version name `system` tells pyenv to use the system Python (detected by
searching your `$PATH`).

When run without a version number, `pyenv global` reports the currently configured
global version.

### install

Install a Python version (using python-build).

```shell
pyenv install 3.12.1
```

#### Options

* `-l`, `--list` - list all available versions of Python including Anaconda, Jython,
pypy and stackless;

```shell
pyenv install --list
```
