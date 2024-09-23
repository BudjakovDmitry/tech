# Installation

Pylint can be installed:

- as a command line tool;
- integrated in your editor/ide;
- as a pre-commit hook;
- for multiple python interpreters in your continuous integration

## Command line installation

```shell
pip install pylint
```

Or if you want to also check spelling with `enchant` (you might need to
[install the enchant C library](
https://pyenchant.github.io/pyenchant/install.html#installing-the-enchant-c-library
)):

```shell
pip install pylint[spelling]
```

## Integration in IDE

- [PyCharm](https://stackoverflow.com/questions/38134086/how-to-run-pylint-with-pycharm/46409649#46409649)
- [Vim](https://www.vim.org/scripts/script.php?script_id=891)

## Pre-commit integration

[...](https://pylint.readthedocs.io/en/latest/user_guide/installation/pre-commit-integration.html)
