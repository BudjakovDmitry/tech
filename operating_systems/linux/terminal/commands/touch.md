# touch

Create file or update file timestamp (update file last modified date and time).

```shell
touch path/to/file
```

Create several files:

```shell
touch a.txt b.txt c.txt
```

Create few files using single command:

```shell
# create files app.py, config.py, views.py
touch {app,config,views}.py
```

## Options

### -d, --date=STRING

Parse STRING and use it as a modification time instead of current time.

```shell
# the last modification date will be (current date - 1 week)
touch todo.txt -d '1 week ago'

# the last modification date will be (current date - 2 month)
touch users.txt -d '2 month ago'

# the last modification date will be (current date - 3 days)
touch cats.txt -d '3 days ago'

# the last modification date will be (current datetime - 10 minutes)
touch pets.txt -d '10 minutes ago'
```
