# systemd

Systemd is an "init system".

The init system is the first and the most important process running on your server. It
has `PID=1`.

It manages all services that run in the background. When you start a process such as
Nginx, the request to start that process is sent to the init system which then starts it
up. Also, init system starts, stops and reloads processes.

__units__ in systemd are resources that it's able to manage. These include services,
timers, mounts, automounts, etc.

Check the status of the unit:

```shell
systemctl status <service>
```

In the output we can see:

```
# this means that service is activce and running
Active: active (running)
```

```
Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
```

In this line `enabled` means that service will start up whet the server is starts up.

If it is `disabled` the server is not going to start up when the server starts up. In
this case you need to start the service manually.

`preset: enabled` means that the distribution has configured systemd such that the new
services will be disabled by default.

## Commands

Start the service manually:

```shell
systemctl start <service>
```

Stop the service manually:

```shell
systemctl stop <service>
```

Restart the service:

```shell
systemctl restart <service>
```

Enable the service:

```shell
systemctl enable <service>
```

Enabled service will start up when the server starts up.

Disable the service:

```shell
systemctl disable <service>
```

## Unit files

Unit files pertain to anything that they can manage. Systemd is looking at unit files to
understand how it needs to interact with processes.

Service file are just text file that contain instructions that tell systemd how it needs
to manage that particular service. Service files have extension of `.service` and can be
found in any of several directories:

1. `/etc/systemd/system`
2. `/run/systemd/system`
3. `/lib/systemd/system` - directory for installed service files.

These directories are ordered from the highest priority down to the lowest. Any service
file that stored in a directory of a higher priority takes the priority. For example any
unit file stored in `/etc/systemd/system` going to take priority over
`/lib/systemd/system`.

There is a number of different types of unit files in these directories: `.service`,
`.target`, `.timer`, etc.

In most cases you don't have to create your own service files, although you can. Most of
the time the service file will be provided by the application that you install. For
example `/etc/systemd/system/apache2.service` comes with apache2.

When you start up your Linux system, it starts systemd and systemd going into these
directories and looking for unit files. If it finds any, it loads them into memory
