# Filesystem

## File system tree

The filesystem is the collection of the files on your machine. It includes the files
needed to run the machine and applications as well as your own files.

Linux organizes its files in a hierarchical directory structure. The top level of the
file system is the root directory `/`. Below this is a tree-like structure of the
directories and files in the system. The filesystem assigns appropriate access rights to
the directories and files.

Unix-like systems such as Linux always have a single file system tree, regardless of how
many drives or storage devices are mounted (attached) to the computer.

The very top of Linux filesystem is the *root directory* (`/`). Some of standard
subdirectories are listed below:

| Directory        | Contains                                                                                                                                                                                                                                                                                                                                             |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `/`              | The root directory, where everything begins.                                                                                                                                                                                                                                                                                                         |
| `/bin`           | System commands, also called *binaries*. Binaries contains the code your machine reads to run programs and execute commands like `ls`, `pwd`, etc.                                                                                                                                                                                                   |
| `/boot` | System boot files, the instructions vital for system startup. Contains the Linux kernel, initial RAM disk image (for drivers needed at boot time), and the boot loader.                                                                                                                                                                                       |
| `/dev` | This is a special directory that contains *device nodes*. "Everything is a file" also applies to devices. Here is where the kernel maintains a list of all the devices it understands. |
| `/etc` | This directory contains all the system-wide configuration files. It also contains a collection of shell scripts that start each of the system services at boot time. Everything in this directory should be readable text. Example: `/etc/crontab` a file that defines when authomated jobs will run; `/etc/passwd` a list of the user accounts; |
| `/home`          | Home directory. User's personal working directory. In this directory users should store their personal files. In normal configurations, each user is given a directory in `/home`. Ordinary users can write files only in their home directories.                                                                                                    |
| `/lib` | Contains shared library files used by the core system programs. |
| `/lost+found` | Each formatted partition or device using a Linux file system, such as ext3, will have this directory. It is used in the case of a partial recovery from a file system corruption event. Unless something really bad has happened to your system, this directory will remain empty. |
| `/media` | Files related to temporary media such as CD or USB drivers that are connected to the system. |
| `/mnt` | On older Linux systems, this directory contains mount points for removable devices that have been mounted manually. |
| `/opt` | This directory is used to install "optional" software. This is mainly used to hold commercial software products that might be installed on the system. |
| `/proc` | It's not a real file system in the sense of files stored on your hard drive. Rather, it is a virtual file system maintained by the Linux kernel. The "files" it contains are peepholes into the kernel itself, The files are readable and will give you a picture of how the kernel sees your computer. |
| `/root` | This is the home directory for the root account. |
| `/sbin`          | This directory contains "system" binaries. These are programs that perform vital system tasks that are generally reserved for the superuser.                                                                                                                                                                                                         |
| `/tmp` | This diretory is intended for the storage of temporary, transient files created by various programs. Some configurations cause this directory to be emptied each time the system is rebooted. |
| `/usr`           | Contains all the programs and support files used by regular users.                                                                                                                                                                                                                                                                                   |
| `/usr/bin`       | Contains the executable programs installed by your Linux distribution. It is not uncommon for this directory to hold thousands of programs.                                                                                                                                                                                                          |
| `/usr/lib`       | The shared libraries for the programs in `/usr/bin`.                                                                                                                                                                                                                                                                                                 |
| `/usr/local`     | This directory tree is where programs that are not included with your distribution but are intended for system-wide use are installed. Programs compiled from source code are normally installed in `/usr/local/bin`. On a newly installed Linux system, this tree exists, but it will be empty until the system administrator puts something in it. |
| `/usr/sbin`      | Contains more system administration programs.                                                                                                                                                                                                                                                                                                        |
| `/usr/share`     | Contains all the shared data used by programs in `/usr/bin`. This includes things such as default configuration files, icons, screen backgrounds, sound fikes, etc.                                                                                                                                                                                  |
| `/usr/share/doc` | Most packages installed on the system will include some kind of documentation. In this directory we will find documentation files organized by package.                                                                                                                                                                                              |
| `/var` | With the exeption of `/tmp`, and `/home` the directories remain relatively static; that is, their contants don't change. The `/var` directory tree is where data that is likely to change is stored. Various databases, spool files, user mail, etc. |
| `/var/log` | Contains log files, records of various system activity. The most useful ones are `/var/log/messages` and `/var/log/syslog`. For security reasons on some systemsm you must be the superuser to view log files. |

The file system layout design is specified in a published standard called the *Linux
Filesystem Hierarchy Standard*. Not all Linux distributions conform to the standard
exactly, but most come pretty close.

## The current working directory

At any given time, we are inside a single directory, and we can see files contained in
the directory and the pathway to the directory above us (parent directory) and any
directories below us. The directory we are standing in is called *current working
directory*. To display the current working directory, we use the `pwd` command.

When we first log in to our system (or start a terminal emulator session), our current
working directory is set to our *home directory*. Each user account is given its own
home directory, and it is the only place a regular user is allowed to write files.

## Path

The path is a human-readable location of a directory or file in Linux file system.

`a/b` structure indicted that the file or directory named "b" is located inside a
directory named "a".

### Special paths

- `~` user's home directory (the default home directory in Linux is `/home/{username}`,
where `username` is the name you would been assigned had you created a personal Linux
user account)
- `/` root directory
- `..` parent of current directory
- `.` current directory

## Wildcards

Because the shell uses filenames so much, it provides special characters to help you
rapidly specify groups of filenames. These special characters are called *wildcards*.
Using wildcards (which is also known as *globbing*) allows you to select filenames based
on patterns of characters.

Wildcards

| Wildcard        | Meaning                       |
|-----------------|-------------------------------|
| `*`             | Matches any characters        |
| `?`             | Matches any single character  |
| `[characters]`  | Matches any character that is a member of the set `characters` |
| `[!characters]` | Matches any characters that is not a member of the set `characters` |
| `[[:class:]]`   | Matches any character that is a member of the specified `class` |

Commonly Used Character Classes

| Character class | Meaning |
|-----------------|---------|
| `[:alnum:]`     | Matches any alphanumeric character |
| `[:alpha:]`     | Matches any alphabetic caracter |
| `[:digit:]`     | Matches any numeral |
| `[:lower:]`     | Matches any lowercase letter |
| `[:upper:]`     | Matches any uppercase letter |

Examples

| Pattern                  | Example                     |
|--------------------------|-----------------------------|
| `*`                      | All files                   |
| `g*`                     | Any file beginning with *g* |
| `b*.txt`                 | Any file beginning with *b* followed by any characters and ending with *.txt* |
| `Data???`                | Any file beginning with *Data* followed by exactly three characters |
| `[abc]*`                 | Any file beginning with either an *a*, *a b*, or *a c* |
| `BACKUP.[0-9][0-9][0-9]` | Any file beginning with *BACKUP.* followed by exactly three numerals |
| `[[:upper:]]*`           | Any file beginning with an uppercase letter |
| `[![:digit:]]*`          | Any file not beginning with a numeral |
| `*[[:lower:]123]`        | Any file ending with a lowercase letter or the numerals *1*, *2* or *3* |

You may have encoutered the `[A-Z]` and `[a-z]` character range notations. These are
traditional Unix notations and worked in older versions of Linux as well. They can still
work, but you have to be careful with them because they will not produce the expected
results unless properly configured. For now, you should avoid using them and use
character classes instead.

## Absolute and relative paths

| path | example                 |
|------|-------------------------|
| **absolute path** is a path from root directory to destination | `/usr/bin/zip`          |
| **relative path** is a path from current directory to destination | `../Documents/node.txt` |

## Important facts about filenames

- Filenames that begin with a period character are hidden. This only means that `ls`
will not list them unless you say `ls -a`.
- Filenames and commands in Linux are case-sensitive. The filenames `File1` and `file1`
refer to different files.
- Do not embed spaces in filenames. If you want to represent spaces between words in a
filename, use underscore characters.
- Linux has no concept of a "file extension". You may name files any way you like. The
contents or purpose of a file is determined by other means. Although Unix-like operating
systems don't use file extensions to determine the contents/purpose of files, many
application programs do.
