# The environment

The shell maintains a set of information during a shell session, known as __the
environment__. It's just a series of key-value pairs that define properties like:

- your home directory;
- your working directory;
- the name of your shell;
- the name of the logged-in user;

and these differ from one session to the next.

Use [printenv](/linux/terminal/commands/printenv.md) to print the environment variables.

The names of these variables are case-sensitive.

## Common used environment

- `USER` - the name of the current user;
- `HOME` - current user's home directory;
- `PWD` - stores current working directory;
- `OLDPWD` - previous location;
