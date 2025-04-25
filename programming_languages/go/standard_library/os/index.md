# os

Package `os` provides a platform-independent interface to operating system
functionality. The design is Unix-like, although the error handing is Go-like; failing
calls return values of type error rather than error numbers. Often, more information is
available within the error.

- [ReadFile](read_file.md)
- [WriteFile](write_file.md)
