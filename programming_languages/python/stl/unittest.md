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

## Organizing test code

The basic building blocks of unit testing are _test cases_ - single scenarios that must
be set up and checked for correctness. In unittest, test cases ate represented by
`unittest.TestCase` instances. To make your own test cases you must write subclasses of
`TestCase` or use `FunctionTestCase`.

```python
import unittest


class DefaultWidgetSize(unittest.TestCase):
    def test_default_widget_size(self):
        widget = Widget('The widget')
        self.assertEqual(widget.size(), (50, 50))
```

In order to test something, we use one of the `assert*` methods provided by the
`TestCase` base class. If the test fails, an exception will be raised with an
explanatory message, and unittest will identify the test case as a _failure_. Any other
exceptions will be treated as _errors_.

We can factor out set-up code by implementing a method called `setUp()`, which the
testing framework will automatically call for every single test we run.


```python
import unittest


class WidgetTest(unittest.TestCase):
    def setUp(self):
        self.widget = Widget('The widget')

    def test_default_widget_size(self):
        self.assertEqual(self.widget.size(), (50, 50), 'incorrect default size')

    def test_widget_resize(self):
        self.widget.resize(100, 150)
        self.assertEqual(self.widget.size(), (100, 150), 'wrong size after resize')
```

> __Note__: The order in which the various tests will be run is determined by sorting
> the test method names with respect to the built-in ordering for strings.

If the `setUp()` method raises an exception while the test is running, the framework
will consider the test to have suffered an error, and the test method will not be
executed.

Similarly, we can provide a `tearDown()` method that tidies up after the test method has
been run:

```python
import unittest


class WidgetTest(unittest.TestCase):
    def setUp(self):
        self.widget = Widget('The widget')

    def tearDown(self):
        self.widget.dispose()
```

If `setUp()` succeeded, `tearDown()` will be run whether the test method succeeded or
not.

Such a working environment for the testing code is called a _test fixture_. A new
TestCase instance is created as a unique test fixture used to execute each individual
test method. Thus `setUp()`, `tearDown()` and `__init__()` will be called once per test.

It is recommended that you use TestCase implementations to group tests together
according to the features they test. unittest provides a mechanism for this: the
_test suit_, represented by unittest's TestSuite class. In most cases, calling
`unittest.main()` will do the right thing and collect all the module's test cases for
you and execute them. However, should you want to customize the building of your test
suite, you can do it yourself:

```python
import unittest


def suite():
    suite = unittest.TestSuite()
    suite.addTest(WidgetTest('test_default_widget_size'))
    suite.addTest(WidgetTest('test_widget_resize'))
    return suite

if __name__ == '__main__':
    runner = unittest.TextTestRunner()
    runner.run(suite())
```
