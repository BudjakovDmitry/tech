# Command-line interface

A CLI interface `dotenv` is also included.

```shell
$ pip install "python-dotenv[cli]"
$ dotenv set USER foo
$ dotenv set EMAIL foo@example.org

$ dotenv list
USER=foo
EMAIL=foo@example.org

$ dotenv list --format=json
{
  "USER": "foo",
  "EMAIL": "foo@example.org"
}
$ dotenv run -- python foo.py
```

Run `dotenv --help` for more information about the options and subcommands.
