# Root User

In Linux systems, there is a superuser called root. The root user can run any command
and access any file on the machine, regardless of the file's actual owner.

The root user has tons of power and could easily damage or even destroy the system by
running the wrong commands.

For this reason, Ubuntu locks the root user by default (that is not the case for all
Linux distributions or Unix like systems, in some systems you can log in as a root user
). But we still have a mechanism to access the root user's power: act as the root user
without actually logging in as the root user.
