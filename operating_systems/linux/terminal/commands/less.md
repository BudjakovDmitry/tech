# less

We can use options inside less prompt. For example, if we want to enable line numbers
when *less* is opened, we can type `-N` and press enter. If we want to disable nine
numbers, we can type `-N` and press enter.

If we want to "jump" to exactly 50% of the way through the file, we can type `50%`.

## Options

### -i, --ignore-case

Causes searches to ignore case. This option is ignored if any uppercase letters appear
in the search pattern (if pattern contains uppercase letters, then that search does not
ignore case).

### -I, --IGNORE-CASE

Like `-i`, but searches ignore case even if the pattern contains uppercase letters.

### -N, --LINE-NUMBERS

Causes a line number to be displayed at the beginning of each line in the display.
