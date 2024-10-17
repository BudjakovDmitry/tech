# os

Miscellaneous operating system interfaces.

This module provides a portable way of using operating system dependent functionality.

## os.kill(pid, sig, /)

Send signal `sig` to the process `pid`. Constants for the specific signals available on
host platform are defined in the [signal](signal.md) module.