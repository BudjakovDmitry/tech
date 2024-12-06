# Nginx

https://nginx.org/

- [Install](install.md)

Nginx has one master process and several worker processes. The main purpose of the
master process is to read and evaluate configuration, and maintain worker processes.
Worker processes do actual processing of requests. Nginx employs event-bases model and
OS-dependent mechanism to efficiently distribute requests among worker processes. The
number of worker processes is defined in the configuration file and may be fixed for a
given configuration or automatically adjusted to the number of available CPU cores.

The way nginx and its modules work is determined in the configuration file. By default,
the configuration file is named `nginx.conf` and placed in the directory
`/usr/local/nginx/conf`, `/etc/nginx/`, or `/usr/local/etc/nginx`.

## Starting, stopping and reloading configuration

To start nginx, run the executable file. Once nginx is started, it can be controlled by
invoking the executable file with the `-s` parameter.

```shell
nginx -s signal
```

Where *signal* may be one of the following:

- `stop` - fast shutdown
- `quit` - graceful shutdown
- `reload` - reloading the configuration file
- `reopen` - reopening the log files

### stop nginx

To stop nginx processes with waiting for the worker processes to finish serving current
requests, execute following command:

```shell
nginx -s quit
```

This command should be executed under the same user that started nginx.

### reload configuration

Changes made in the configuration file will not be applied until the command to reload
configuration is sent to nginx or it is restarted.

To reload configuration execute:

```shell
nginx -s reload
```

Once the master process receives the signal to reload configuration, it checks the
syntax validity of the new configuration file and tries to apply the configuration. If
this is a success, the master process starts new worker processes and send messages to
old worker processes, requesting them to shut down. Otherwise, the master process rolls
back the changes and continues to work with the old configuration. Old worker processes,
receiving a command to shut down, stop accepting new connections and continue to service
current requests until all such requests are serviced. After that, the old worker
processes exit.

A signal may also be sent to nginx processes with the help of Unix tools such as the
`kill` utility. In this case a signal is sent directly to a process with a given process
ID. The process ID if the nginx master process is written, by default, to the
`nginx.pid` in the directory `/usr/local/nginx/logs` or `/var/run`. For example:

```shell
# send QUIT (graceful shutdown) signal to master process with ID = 1628
kill -s QUIT 1628
```

For getting the list of all running nginx processes, the `ps` utility may be used.

```shell
ps -ax | grep nginx
```
