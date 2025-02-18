# unittest - Unit testing framework

__test fixture__ - a _test fixture_ represent the preparation needed to perform one or
more tests, and any associated cleanup actions. This may involve, for example, creating
temporary or proxy databases, directories, or starting a server process.

__test case__ - the individual unit of testing. It checks for a specific response to a
particular set of inputs. Unittest provides a base class `TestCase`, which may be used
to create a new test cases.

__test suite__ - a collection of test cases, test suites, or both. It is used to
aggregate tests that should be executed together.

__test runner__ - a component which orchestrates the execution of tests and provides the
outcome to the user.

## Basic example

```python
import unittest

class TestStringMethods(unittest.TestCase):

    def test_upper(self):
        self.assertEqual('foo'.upper(), 'FOO')

    def test_isupper(self):
        self.assertTrue('FOO'.isupper())
        self.assertFalse('Foo'.isupper())

    def test_split(self):
        s = 'hello world'
        self.assertEqual(s.split(), ['hello', 'world'])
        # check that s.split fails when the separator is not a string
        with self.assertRaises(TypeError):
            s.split(2)

if __name__ == '__main__':
    unittest.main()
```

A testcase is created by subclassing `unittest.TestCase`.

The three individual tests are defined with methods whose names start with the letters
`test`. This naming convention informs the test runner about which methods represent
tests.

`unittest.main()` provides a command-line interface to the test script. It is a simple
way to run tests.

Passing the `-v` option will enable the verbose mode.

```shell
python -m unittest -v test_module
```

The `setUp()` and `tearDown()` methods allow you to define instructions that will be
executed before and after each test method.

## Command-Line Interface

The unittest module can be used from the command line to run tests from modules, classes
or even individual test methods:

```shell
python -m unittest test_module1 test_module2
python -m unittest tests/test_something.py  # test modules can be specified by the path
python -m unittest test_module.TestClass
python -m unittest test_module.TestClass.test_method
```

You can pass in a list with any combinations of module names, any fully qualified class
or method names.

The file specified must still be importable as module. The path is converted to a module
name by removing the '.py' and converting path separators into '.'. If you want to
execute a test file that isn't importable as a module you should execute the file
directly instead.

When executed without arguments `Test Discovery` is started:

```shell
python -m unittest
```

Show a list of all the command-line options:

```shell
python -m unittest -h
```
