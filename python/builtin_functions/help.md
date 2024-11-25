# help

Invoke the built-in help system.

* If no arguments is given, the interactive help system starts on the interpreter
console.
* If the argument is a string, then the string is looked up as the name of the module,
function, class, method, keyword, or documentation topic, and a help page is printed on
the console.
* If the argument is any kind of object, a help page in the object is generated.

Press `q` to exit the help.

```python
help("return")
help(help)
help(123)
```
