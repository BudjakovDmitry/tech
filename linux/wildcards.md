# Wildcards and character classes

Wildcards is a special characters which help rapidly specify group of characters.

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

| Pattern                  | Example                                                                       |
|--------------------------|-------------------------------------------------------------------------------|
| `*`                      | All files                                                                     |
| `g*`                     | Any file beginning with *g*                                                   |
| `b*.txt`                 | Any file beginning with *b* followed by any characters and ending with *.txt* |
| `Data???`                | Any file beginning with *Data* followed by exactly three characters           |
| `[abc]*`                 | Any file beginning with either an *a*, *b*, or *c*                            |
| `BACKUP.[0-9][0-9][0-9]` | Any file beginning with *BACKUP.* followed by exactly three numerals          |
| `app[2-4].js`            | *app2.js*, *app3.js*, *app4.js*                                               |
| `[[:upper:]]*`           | Any file beginning with an uppercase letter                                   |
| `[![:digit:]]*`          | Any file not beginning with a numeral                                         |
| `*[[:lower:]123]`        | Any file ending with a lowercase letter or the numerals *1*, *2* or *3*       |

You may have encoutered the `[A-Z]` and `[a-z]` character range notations. These are
traditional Unix notations and worked in older versions of Linux as well. They can still
work, but you have to be careful with them because they will not produce the expected
results unless properly configured. For now, you should avoid using them and use
character classes instead.

