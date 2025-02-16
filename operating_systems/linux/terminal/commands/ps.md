# ps

Return currently running processes and their IDs. ps stands for "process status".

The example of `ps` output:

```
PID    TTY    TIME      CMD
2925   pts/0  00:00:00  bash
12968  pts/0  00:00:00  ps
```

Possible columns within the output:

- `PPID` refers to parent process id (this column appear in hierarchical view).
- `PID` - process id. Each process on a Linux system is going to have its own unique
process id.
- `PGID` refers to the parent group process id (in hierarchical view).
- `SID` - session id. This is usually the same as the process that started the chain.
- `TTY` refers to the terminal that the process is running inside of. If a process is
started as a part of a specific terminal, it's going to show terminal in this column
(for example `tty2`). If process was started by the system, it's going to show a
question mark instead (`?`).
- `TPGID` refers to the terminal session id with which the process is associated. If
there isn't a terminal that's associated with the process then `-1` will be displayed
instead.
- `STAT`
  - `s`. this is a process leader or root process. Sometimes there's a process that
  starts another process creating kind of process tree. `s` means that it's a process
  leader.
  - `S` means that the process is running in uninterruptible sleep which essentially
  means that it's waiting for some sort of user input and can't be disturbed until it
  receives that.
  - `R` actively running process.
  - `T` process is stopped.
- `UID` the user id that started that particular process (UID=0 is a root )
- `TIME` refers to CPU time. How much time the process has been utilizing the CPU;
- `CMD` the command that is running as part of that process;

By default, the output only contains the processes that are owned by you and that are
running as a part of this particular terminal session. That means you'll get different
output between different terminals depending on that you're running inside those
terminals.

## Examples

```shell
# all processes that you're running:
ps x

# show process hierarchy
ps -He

# show process hierarchy
ps -axjf

ps -aux
```

## Options

### -e

List all processes running on the system, regardless of which user started them.

## -H

Show process hierarchy
