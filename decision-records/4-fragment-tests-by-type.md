# Fragment tests by type

## Context
Running certain types of tests is expensive, and only gets more expensive over time as the number of tests grows.

Teams must strive to create as fast of a feedback loop as possible, to maximize productivity and minimize developer frustration.

## Decision
We will fragment tests by their type.

The `tests` directory of a project will look like this:
```sh
tests
└── acceptance
├── functional
├── performance
├── property
├── security
├── smoke
├── unit
```

Additional test types can be added as required.

## Consequences
The tool used to run tests must support running only the tests under a particular directory.

Developers may run just the fast tests locally as they're developing, to speed up their feedback loop, then offload the rest of the test suite to be run on CI/CD.

Tests can be parallelized better in CI/CD.
