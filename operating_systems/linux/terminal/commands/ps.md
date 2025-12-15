# ps

The example of `ps` output:

```
PID    TTY    TIME      CMD
2925   pts/0  00:00:00  bash
12968  pts/0  00:00:00  ps
```

Possible columns within the output:

- `PPID` refers to parent process id (this column appear in hierarchical view).
- `PGID` refers to the parent group process id (in hierarchical view).
- `SID` - session id. This is usually the same as the process that started the chain.
- `TPGID` refers to the terminal session id with which the process is associated. If
there isn't a terminal that's associated with the process then `-1` will be displayed
instead.
- `STAT`
  - `s`. this is a process leader or root process. Sometimes there's a process that
  starts another process creating kind of process tree. `s` means that it's a process
  leader.
- `UID` the user id that started that particular process (UID=0 is a root )
- `TIME` refers to CPU time. How much time the process has been utilizing the CPU;
- `CMD` the command that is running as part of that process;

## Examples

```shell
# show process hierarchy
ps -He

# show process hierarchy
ps -axjf
```

## Options

### -e

List all processes running on the system, regardless of which user started them.

## -H

Show process hierarchy
