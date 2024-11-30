# uname

Return the operating system name. `uname` stands for "Unix name".  Returns the OS
information such as kernel name and version number. This can be useful to identify type
of the system you are working on or diagnose system-related issues.

```shell
uname
Linux
```

## Options

### -a

Print all information, in the following order, except omit `-p` and `-i` if unknown:
`-s`, `-n`, `-r`, `-v`, `-m`, `-p`, `-i`, `-o`.

### -i

Print the hardware platform.

### -m, --machine

Print the machine hardware name. The reason why you might want to run this particular
command is to find out what your CPU architecture is.

```shell
uname -m
x86_64
```

### -n, --nodename

Print the network node hostname. Returns the same result as `hostname` command.

### -o, --operating-system

Print the operating system.

```shell
uname -o
GNU/Linux
```

### -p

Print the processor type.

### -r, --kernel-release

Print the kernel release version.

```shell
uname -r
5.15.0-124-generic
```

### -s

Print the kernel name.

### -sr

Return both the OS name and its version.

### -v, --kernel-version

Detailed information about OS.

```shell
uname -v
#134-Ubuntu SMP Fri Sep 27 20:20:17 UTC 2024
```
