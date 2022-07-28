# Python code style

## Context
Debates around code style are usually fruitless and only serve to cause noise and frustration.

Standardized formatting rules enable individuals to contribute changes across codebases owned by other, or multiple, teams.

A reasonable code style should be standardized once, and tooling used to enforce it.

## Decision
We will use 120 character length line limits.

We will use [black](https://github.com/psf/black) to format `.py` files with `--line-length 120` option.

We will use [isort](https://github.com/PyCQA/isort) to sort imports in `.py` files with `--force-single-line-imports` and `--force-sort-within-sections` options.

The aforementioned rules will be implemented in the `python-sdk` cli utility, under the `fmt` command.

## Consequences
Lines that approach the 120 character length, may not be viewable on smaller screens if two editors windows are open side by side.

Debates around code style, be they in person or in peer reviews, will be cut short by referencing this decision record

Developers can write code in whatever style they prefer, allowing formatting tools to reformat their code before checking it in.
