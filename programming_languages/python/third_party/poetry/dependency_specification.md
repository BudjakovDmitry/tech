# Dependency specification

## Version constraints

### Extract requirements

You can specify the exact version of a package.

`1.2.3` is an example of an exact version specification.

This will tell Poetry to install this version and this version only. If other
dependencies require a different version, the solver will ultimately fail and abort any
installation or update procedures.

Exact versions can also be specified with `==` according to
[PEP 440](https://peps.python.org/pep-0440/). `==1.2.3` is an example of this.
