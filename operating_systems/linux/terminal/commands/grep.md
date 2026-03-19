# grep

Common usage pattern:

```shell
grep pattern filename
```

## Options

### -A NUM, --after-context=NUM

Print NUM lines of trailing context after matching lines.

### -B NUM, --before-context=NUM

Print NUM lines of leading context before matching lines.

### -C NUM, -NUM, --context=NUM

Print NUM lines of output context (NUM lines before and NUM lines after matching lines).

### -E, --extended-regexp

Interpreter patterns as extended regular expressions.

**Basic vs Extended Regular Expressions**: in basic regular expressions the
meta-characters *?*, *+*, *{*, *|*, *(* and *)* lose their special meaning; instead use
the backslashed versions *\?*, *\+*, *\{*, *\|*, *(* and *\)*.

```shell
# match lines with question mark
grep "?" file
```

### -I

Process a binary file as if it did not contain matching data; this is equivalent to the
`--binary-files=without-match`.

### -c

Get the count of matching lines;

### -l, --files-with-matches

Suppress normal output; instead print the name of each input file from which output
would normally have been printed. Scanning each input file stops upon first match.

### -m NUM, --max-count=NUM

Stop reading a file after NUM matching lines.

### -w

Match only if the pattern matches whole words rather than fragments located inside of
the words.

## Piping to grep

A common use case is to use `grep` to whittle down or filter a large chunk of data. For
example:

```shell
# this command lets us see python processes
ps -aux | grep "python"
```
