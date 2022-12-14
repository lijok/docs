# Make task runner

## Context
A simple task runner is required to abstract away the disparate implementations of the common tasks that are run on various codebases: setup, test, package, publish, etc.

As the task runner is the one setting environments up, it itself must require no setup. Therefore it must either come pre-installed on the OS, or be installable through the OS's package manager.

A task runner must be:
- Easy to read tasks
- Easy to extend with new tasks
- Widely used by the industry and well documented

## Decision
Use GNU Make as a task runner.

## Consequences
Make comes pre-installed and works out of the box on MacOS and most Linux distros.

All tasks sit in a single `Makefile`, use little to no boilerplate and are written using basic shell commands.

The same task runner can be called in CI/CD systems.

GNU Make has no Windows support. If native Windows support is required (no wsl), a separate `make.ps1` script has to be maintained, emulating Makes behaviour, resulting in duplicated effort.
