# cal, ncal

Display a simple calendar in traditional format.

ncal stands for "new cal". There is also a `cal` command that does the same exact thing,
but `ncal` adds some functionality.

## Arguments

If you pass a year in `cal` or `ncal` it will print out the calendar for that entire
year

```shell
cal 2019
ncal 2024
```

If we specify a month and a year, they will print out that month's calendar.

```shell
cal april 1927
ncal may 1990
```

## Options

### -A

Display a certain number of months after a specific date.

```shell
ncal -A 2
# or
ncal -A2
```

This option can be combined with `-B` option to get *n* months before and *m* months
after the specific date.

### -B

Print a number of months before the specific date.

```shell
cal -B1
```

This option can be combined with `-A` option to get *n* months before and *m* months
after the specific date.

### -h

This option is only for `ncal`.

By default, today's date is highlighted. `-h` option turns off the highlighting.

### -j

Tells `cal` or `ncal` to display a calendar using Julian days (days are numbered
starting from January 1st).

### -M

This option is only for `ncal`

Tell `ncal` to use Monday as the first day of the week instead of Sunday (normally,
Sunday is a first day).

### -w

Print the number of the week below each week column.

### -3

Tells `cal` or `ncal` to display the previous, current and next month.
