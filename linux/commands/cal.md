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

### -3

Tells `cal` or `ncal` to display the previous, current and next month.
