# Package managers

Both software updates and software installation files for Linux operating systems are
distributed in files known as **packages**. These packages are archive files containing
the required components for either installing new software or updating existing
software. You use **package mangers** to manage the download and installation of
packages. Different Linux distros provide different package managers. **DEB** and
**RPM** packages are used by package managers in Linux operating systems. They are
distinct file types containing software or updates for different Linux operating
systems.

Package managers can automatically resolve dependencies between packages. They can
notify you when updates are available.

Package managers benefits:

- they can automatically resolve dependencies between packages;
- they can notify you when updates are available;
- they can automatically install updates or let you select and install just the ones you
want.

## Packages

`.deb` files are used for Debian-based distributions such as Debian, Ubuntu and Mint.
deb stands for Debian.

`.rpm` files are used for Red Hat-based distributions such as CentOS, Rad Hat Enterprise
Linux (RHEL), Fedora, and openSUSE. rpm stands for Red Hat Package Manager.

Deb and RPM formats are equivalent, so the contents of the file can be used on other
type of Linux OSs. If you find that a package that you want to use is only available in
the other format, you can convert it, using the **alien tool**.

```
# rpm to deb
alien <package-name>.rpm

# deb to rpm
alien -r <package-name>.deb
```

### apt

apt (Advanced Packaging Tool) is a command-line tool for updating deb-based Linux
systems.

apt sources are located a `/etc/apt`.

Before installing or updating any packages on Linux system, it's best practice to update
your package list index.

```shell
sudo apt update
```

Running this command ensures all of your package dependencies are up-to-date prior to
making any changes to your system's packages.

apt uses file `/etc/apt/sources.list` to access the sources of package index files.

To install some tool enter:

```shell
sudo apt install <package-name>
```

```shell
# install the packages which can be upgraded
sudo apt upgrade

# upgrade specific package (for example nano)
sudo apt upgrade nano
```

### yum

yum is a command-line tool for updating RPM-based systems. yum stands for Yellowdog
Updater, Modified. To update all packages in the system type:

```shell
sudo yum update
```

Install a package:

```shell
sudo yum install <package-name>
```
