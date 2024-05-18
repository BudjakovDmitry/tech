# Wildcards and character classes

Wildcards is a special characters which help rapidly specify group of characters.

## Wildcards

| Wildcard        | Meaning                                                                            |
|-----------------|------------------------------------------------------------------------------------|
| `*`             | Matches any characters                                                             |
| `?`             | Matches any single character                                                       |
| `[characters]`  | Matches any character that is a member of the set `characters`                     |
| `[!characters]` | Matches any characters that is not a member of the set `characters`                |
| `[[:class:]]`   | Matches any character that is a member of the specified `class`                    |
| `^`             | Inside of square brackets (`[]`) we can specify a range of characters to not match |

## Character classes

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
| `[A-C]*`                 | Any file beginning with either capital *A*, *B* or *C*                        |
| `[[:upper:]]*`           | Any file beginning with an uppercase letter                                   |
| `[![:digit:]]*`          | Any file not beginning with a numeral                                         |
| `*[[:lower:]123]`        | Any file ending with a lowercase letter or the numerals *1*, *2* or *3*       |
| `[^a]*`                  | Any files that do not start with "a"                                          |
| `[^0-9]*`                | Any files that do not start with a number (0-9)                               |

You may have encountered the `[A-Z]` and `[a-z]` character range notations. These are
traditional Unix notations and worked in older versions of Linux as well. They can still
work, but you have to be careful with them because they will not produce the expected
results unless properly configured. For now, you should avoid using them and use
character classes instead.

## Brace expansion

Brace expansion is used to generate arbitrary strings. Basically is uses to generate
multiple strings for us based on a pattern. We provide a set of strings inside curly
braces (`{}`), as well as optional surrounding prefixes and suffixes.

The specified strings are used to generate all possible combinations with the optional
prefixes and suffixes.

### Examples

```shell
echo {1,2,3}
# 1 2 3
```

```shell
touch page{1,2,3}.txt
# will create three new files: page1.txt page2.txt page3.txt
```

```shell
touch May_{Mon,Tue,Wed,Thu,Fri}_TODO.txt
# will create five files: May_Mon_TODO.txt, May_Tue_TODO.txt, ... May_Fri_TODO.txt
```

We can use multiple sets of curly braces in one pattern. In this case we will get every
possible combination:

```shell
echo {Mon,Tue,Wed,Thu,Fri}_{AM,PM}.txt
# Mon_AM.txt Mon_PM.txt Tue_AM.txt Tue_PM.txt Wed_AM.txt Wed_PM.txt Thu_AM.txt
# Thu_PM.txt Fri_AM.txt Fri_PM.txt
```

#### Ranges

We can provide a numeric range, which will be used to generate a sequence.

```shell
touch Jan{1..31}.txt
# will generate Jan1.txt, Jan2.txt, ... Jan31.txt
```

Reverse range:

```shell
echo {10..0}
# 10 9 8 7 6 5 4 3 2 1 0

echo {f..a}
# f e d c b a
```

We can provide a third value which defines the interval for the range.

```shell
touch {0..10..2}
# 0 2 4 6 8 10
```

We can even specify alphabetical ranges:

```shell
echo group_{A..F}.txt
# group_A.txt group_B.txt group_C.txt group_D.txt group_E.txt group_F.txt
```

Create a complex directory structure with nested directories in one command:

```shell
mkdir -p {Mon,Tue,Wed,Thu,Fri,Sat,Sun}/{Morning,Afternoon,Evening}
```

It will create next structure:

```
/path/to/current/directory/
|--Mon
|  |--Morning/
|  |--Afternoon/
|  |--Evening/
|
|--Tue/
|  |--Morning/
|  |--Afternoon/
|  |--Evening/
|
|--Wed/
|  |--Morning/
|  |--Afternoon/
|  |--Evening/
|
|--Thu/
|  |--Morning/
|  |--Afternoon/
|  |--Evening/
|
|--Fri/
|  |--Monday/
|  |--Afternoon/
|  |--Evening/
|
|--Sat/
|  |--Monday/
|  |--Afternoon/
|  |--Evening/
|
|--Sun/
|  |--Monday/
|  |--Afternoon/
|  |--Evening/
```

#### Nested brace expansion

```shell
echo {x,y{1..5},z}
# x y1 y2 y3 y4 y5 z
```

```shell
echo {x,y{1..3}.{red,blue},z}
# x y1.red y1.blue y2.red y2.blue y3.red y3.blue z
```

## Arithmetic expansion

The shell performs arithmetic via expansion using the `$((math_expression))` syntax.
Inside the parentheses, we can write arithmetic expressions using:

* `+` addition
* `-` subtraction
* `*` multiplication
* `/` division
* `**` exponentation
* `%` modulo (remainder operator)

```shell
echo $((10+7))
# 17

echo $((10-3))
# 7

echo $((3*13))
# 39

echo $((2**10))
# 1024

echo $((10%3))
# 1
```

The shell only performs integer arithmetic, so the result is always an integer number.

```shell
echo $((10/3))
# 3
```

We can use more complicated expressions and use parentheses to change the order.

```shell
echo $((5+4*2))
# 13

echo $(((5+4)*2))
# 18
```
