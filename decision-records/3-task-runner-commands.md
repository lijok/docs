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
- test-all-versions
- acceptance-test
- integration-test
- load-test
- performance-test
- property-test
- system-test
- unit-test
- lint
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
    test-all-versions: Run all tests on all supported versions
    acceptance-test:   Run acceptance tests
    integration-test:  Run integration tests
    load-test:         Run load tests
    performance-test:  Run performance tests
    property-test:     Run property tests
    system-test:       Run system tests
    unit-test:         Run unit tests
    lint:              Run the linters
    fmt:               Format the codebase
    package:           Package
    publish:           Publish
    install:           Install
    clean:             Cleanup
```

Additional, project specific commands, should be avoided where possible. If absolutely required, such commands must come after the aforementioned ones.

## Consequences
Workflows between projects remain consistent, reducing the time it takes to onboard a new team member.

New tools to back certain commands can be introduced more easily as the training cost for the wider team is massively reduced.

Commands can be reused in CI/CD, facilitating simpler workflows.

Some of the test commands (`system-test`, `acceptance-test`, etc), may not be implemented as no such tests may exist on a particular project. In such cases, the command should simply output `Nothing to do` and successfully exit.