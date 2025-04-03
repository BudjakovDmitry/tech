# kill

Send signal to a process.

```
kill [options] <pid> [...]
```

A _signal_ is a message sent to a process to interrupt it and cause a response. If the
process has been designed to respond to signals of the type sent it does so; otherwise,
it terminates.

Some commonly used signals and their meanings:

| Signal number | Signal name | Meaning |
|---------------| ----------- | ------- |
| 1             | HUP         | Hangup (reread the configuration file) |
| 2             | INT         | Interrupt (same as pressing Control+C in a terminal session) |
| 9             | KILL        | Kill (terminates without cleanup). Only works if issued by process owner or super user (root). The program cannot respond to this signal; it must terminate. |
| 15 (default)  | TERM        | Kill (terminate gracefully after cleanup). Only works if issued by process owner or super user (root) |

Sending signal #9 to a process is a last resort. Don't do that unless you absolutely
have to because signal #9 kill the process immediately without any checks.

It is strongly recommended to send signal #15 first. A lot of times processes will have
a cleanup procedure that they execute when they close. When we use signal #15 this
procedure will be executed (with signal #9 not).

## Options

### -L

List the available signal choices in a nice table.

## Examples

```shell
# send SIGKILL signal to process with PID=45622
kill -9 45622
```
