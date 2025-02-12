# runserver

Starts a lightweight development web server on the local machine. By default, the server
runs on port 8000 on the IP address `127.0.0.1`. You can pass in an IP address and port
number explicitly.

If you run this script as a user with normal privileges (recommended), you might not
have access to start a port on a low port number. Low port numbers are reserved for the
superuser (root).

This server uses the WSGI application object specified by the `WSGI_APPLICATION`
setting.

The development server automatically reloads Python code for each request, as needed.
You don’t need to restart the server for code changes to take effect. However, some
actions like adding files don’t trigger a restart, so you’ll have to restart the server
in these cases.

If you’re using Linux or MacOS and install both
[pywatchman](https://pypi.org/project/pywatchman/) and the
[Watchman](https://facebook.github.io/watchman/) service, kernel signals will be used to
autoreload the server (rather than polling file modification timestamps each second).
This offers better performance on large projects, reduced response time after code
changes, more robust change detection, and a reduction in power usage. Django supports
pywatchman 1.2.0 and higher.

> **Large directories with many files may cause performance issues**
> 
> When using Watchman with a project that includes large non-Python directories like
> node_modules, it’s advisable to ignore this directory for optimal performance. See the
> watchman documentation for information on how to do this.

> **Watchman timeout**
> 
> `DJANGO_WATCHMAN_TIMEOUT`
>
> The default timeout of Watchman client is 5 seconds. You can change it by setting the
> DJANGO_WATCHMAN_TIMEOUT environment variable.

When you start the server, and each time you change Python code while the server is
running, the system check framework will check your entire Django project for some
common errors (*django-admin check*). If any errors are found, they will be printed to
standard output. You can use the `--skip-checks` option to skip running system checks.

You can run as many concurrent servers as you want, as long as they’re on separate ports
by executing *django-admin runserver* more than once.

To make your development server viewable to other machines on the network, use its own
IP address (e.g. 192.168.2.1), 0 (shortcut for 0.0.0.0), 0.0.0.0, or :: (with IPv6
enabled).

You can provide an IPv6 address surrounded by brackets (e.g. *[200a::1]:8000*). This
will automatically enable IPv6 support.

A hostname containing ASCII-only characters can also be used.

If the staticfiles contrib app is enabled (default in new projects) the *runserver*
command will be overridden with its own runserver command.

## Options

### --noreload

Disables the auto-reloader. This means any Python code changes you make while the server
is running will not take effect if the particular Python modules have already been
loaded into memory.

### --nothreading

Disables use of threading in the development server. The server is multithreaded by
default.

### --ipv6, -6

Uses IPv6 for the development server. This changes the default IP address from
*127.0.0.1* to *::1*.

## Examples

```shell
# Port 8000 on IP address 127.0.0.1
django-admin runserver

# Port 8000 on IP address 1.2.3.4
django-admin runserver 1.2.3.4:8000

# Port 7000 on IP address 127.0.0.1
django-admin runserver 7000

# Port 8000 on IPv6 address ::1
django-admin runserver -6

# Port 7000 on IPv6 address ::1
django-admin runserver -6 7000

# Port 7000 on IPv6 address 2001:0db8:1234:5678::9
django-admin runserver [2001:0db8:1234:5678::9]:7000

# Port 8000 on IPv4 address of host localhost
django-admin runserver localhost:8000

# Port 8000 on IPv6 address of host localhost
django-admin runserver -6 localhost:8000
```

## Serving static files with the development server

By default, the development server does not serve any static files for your site (such
as CSS files, images, things under MEDIA_URL and so forth).

## Serving with ASGI in development

Django’s runserver command provides a WSGI server. In order to run under ASGI you will
need to use an ASGI server. The Django Daphne project provides Integration with
runserver that you can use.
