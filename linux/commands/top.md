# top

Displays a table of running processes or threads and resource usage including memory,
CPU and IO. Top stands for "table of processes".

To quit from top press `q`.

By default, tasks are sorted by CPU usage. You can press the following keys with *shift*
while top is running to sort the table:

| Key | Sorts by |
|-----|----------|
| `m` | Memory usage |
| `p` | CPU usage |
| `n` | Process ID (PID) |
| `t` | Running time |

## Options

### -n

Exit automatically after a specified number of repetitions.

```shell
top -n 10
```
