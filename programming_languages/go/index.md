# GO programming language

## Download and install (Linux)

Download Go from [official site](https://go.dev/dl/).

1. Remove any previous Go installation by deleting the `/usr/local/go` folder (if it
exists), then extract the archive you downloaded into `/usr/local`, creating a fresh Go
tree in `/usr/local/go`:

```shell
$ rm -rf /usr/local/go && tar -C /usr/local -xzf go1.24.0.linux-amd64.tar.gz
```

You may need to run the command as root.

__Do not__ untar the archive into an existing `/usr/local/go` tree. This is known to
produce broken Go installations.

2. Add `/usr/local/go/bin` to the `PATH` environment variable.

You can do it by adding the following line to your `$HOME/.profile` or `/etc/profile`
(for a system-wide installation)

```shell
export PATH=$PATH:/usr/local/go/bin
```

And then execute `.profile` script to apply changes:

```shell
source $HOME/.profile
```

3. Verify that you've installed Go by typing

```shell
go version
```

4. Confirm that the command prints the installed version of Go.
