# Simple CI/CD workflows

## Context
CI/CD workflows are very difficult to test, as mature tooling for written, reproducible CI/CD workflow testing does not exist. Therefore, the only way to test your CI/CD workflows is to make changes to them, push, and hope for the best. This gets particularly tricky and dangerous if you have to test CI/CD workflows that manage deployments.

CI/CD is one of the most in-flux systems in any company. Migrations to a different CI/CD system happen every couple of years, as new, cheaper, more convenient alternatives come out.

Migrating to a different CI/CD tool is a difficult organization-wide exercise, especially if its workflows are stored individually in each projects repository.

A lot of CI/CD workflows tend to be identical to workflows that developers run when writing code (setup, testing, packaging, installation, etc).

## Decision
We will offload all CI/CD workflow logic outside of the workflow file, and into task runner commands.

We will utilize CI/CD simply for invoking a script, on a parallelized environment, in response to events.

An example of a simple, parallelized GitHub Actions CI/CD workflow:
```yml
name: test
on:
  pull_request:
  push:
    branches:
      - master


jobs:
  test:
    name: ${{ matrix.test-type }} ${{ matrix.os }} python${{ matrix.python-version }}
    runs-on: ${{ matrix.os }}

    strategy:
      fail-fast: true

      matrix:
        os:
          - ubuntu-latest
          - macos-latest
          - windows-latest
        python-version:
          - "3.8"
          - "3.9"
          - "3.10"
        test-type:
          - "acceptance-test"
          - "functional-test"
          - "integration-test"
          - "performance-test"
          - "property-test"
          - "security-test"
          - "system-test"
          - "unit-test"

    steps:
      - name: checkout repo
        uses: actions/checkout@v3

      - name: install python${{ matrix.python-version }}
        uses: actions/setup-python@v4
        with:
          python-version: ${{ matrix.python-version }}

      - name: cache python dependencies
        uses: actions/cache@v3
        with:
          path: .venv
          key: python-${{ matrix.python-version }}-${{ matrix.os }}-${{ hashFiles('pyproject.toml') }}

      - name: run tests
        run: make ${{ matrix.test-type }}
        env:
          PYTHON_VERSION: ${{ matrix.python-version }}
```

## Consequences
CI/CD workflows require minimal testing, and invoked scripts can be tested locally.

Migrations between CI/CD tools can be undertaken more easily.

Standardized CI/CD workflows can be deployed to repositories as part of its initialization.
