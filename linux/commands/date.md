# date

Print current system date and time.

```shell
date
Sat 30 Dec 2023 09:20:43 UTC
```

You can format an output.

```shell
date "+%j day of %Y"
# 364 day of 2023

date "+It's a %A, the %j day of %Y"
# It's Saturday, the 364 day of 2023

date "+%D"
# 01/04/24
```

Here are some popular format specifiers:

| Specifier | Explanation |
|-----------|-------------|
| `%d` | Displays the day of the month (01 to 31) |
| `%h` | Displays the abbreviated month name (Jan to Dec) |
| `%m` | Displays the month of a year (01 to 12) |
| `%Y` | Displays the four-digit year |
| `%T` | Displays the time in 24 hour format as HH:MM:SS |
| `%H` | Displays the hour |

## Options

### -r or --reference=FILE

Display the last modification time of FILE.

```shell
date -r /path/to/file
date --reference=/path/to/file
```

### -u

Long format: `--universal`

Print the date in Coordinated Universal Time (UTC).
