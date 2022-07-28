# Python package interface in init

## Context
Excessive documentation, especially around package usage, leads to adoption problems.

Good packages are designed for easy consumption and familiarization.

If package exports are easily discoverable, developers have to rely less on documentation.


## Decision
We will expose the interface of packages in `__init__.py`.


## Consequences
Packages can be imported like: `from python_sdk import log` to make all exports available.

Consumers can easily discover what exports are available to them.

Package interface will be self documenting.

Busywork is required to add imports to `__init__.py` files.
