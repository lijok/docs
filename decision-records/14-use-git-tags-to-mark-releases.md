# Use Git tags to mark releases

## Context
Releases can be automated by triggering CI/CD builds off of a git tag, or a push to master.

Complex git workflows such as Git Flow have made their way into the mainstream as a result of lacking automation around releases.

## Decision
We will mark releases by tagging commits with their version number.

## Consequences
In most cases, master is not reflective of the latest release. The relevant git tag has to be looked up instead.
