# Task runner commands

## Context
Onboarding new team members onto projects requires unnecessary, extensive downtime as they figure out how to setup the project, its environment, how to run its tests, etc.

Most projects, while using potentially different tools, have the same workflows:
 - Setup the environment
 - Package and install the project into the environment
 - Run tests against the project
 - Package the project and publish it

## Decision
We will implement the following commands in the task runner on all projects:
- help
- setup
- test
- test-all
- acceptance-test
- functional-test
- performance-test
- property-test
- security-test
- smoke-test
- unit-test
- fmt
- package
- publish
- install
- clean

The output of the help command should look like this:
```sh
Available commands:

    help:              Show this page
    setup:             Setup the environment
    test:              Run fast tests
    test-all:          Run all tests
    unit-test:         Run unit tests
    property-test:     Run property tests
    functional-test:   Run functional tests
    security-test:     Run security tests
    smoke-test:        Run smoke tests
    acceptance-test:   Run acceptance tests
    performance-test:  Run performance tests
    fmt:               Format the codebase
    package:           Package
    publish:           Publish
    install:           Install
    clean:             Cleanup
```

We will avoid additional, project specific commands where possible. If absolutely required, such commands must come after the aforementioned ones.

If project specific commands are required, the output of the help command should look like this (`test-all-versions` and `debug` being used as example commands):
```sh
Available commands:

    help:              Show this page
    setup:             Setup the environment
    test:              Run fast tests
    test-all:          Run all tests
    unit-test:         Run unit tests
    property-test:     Run property tests
    functional-test:   Run functional tests
    security-test:     Run security tests
    smoke-test:        Run smoke tests
    acceptance-test:   Run acceptance tests
    performance-test:  Run performance tests
    fmt:               Format the codebase
    package:           Package
    publish:           Publish
    install:           Install
    clean:             Cleanup


Project-specific commands:

    test-all-versions: Run all tests on all supported versions
    debug:             Start interactive debugger
```

## Consequences
Workflows between projects remain consistent, reducing the time it takes to onboard a new team member.

New tools to back certain commands can be introduced more easily as the training cost for the wider team is massively reduced.

Commands can be reused in CI/CD, facilitating simpler workflows.

Some of the test commands (`smoke-test`, `acceptance-test`, etc), may not be implemented as no such tests may exist on a particular project. In such cases, the command should simply output `Nothing to do` and successfully exit.

Project specific commands immediately stand out as they are not normally present.

Developers can run `make test` in projects and expect a short feedback loop as the command only runs fast tests.
