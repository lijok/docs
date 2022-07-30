# Use Git tags to mark releases

## Context
Releases can be automated by triggering CI/CD builds off of a git tag, or a push to master.

Complex git workflows have made their way into the mainstream as a result of lacking automation around releases.

## Decision
We will mark releases by tagging commits with their version number.

## Consequences
Master will not be reflective of the latest release in most cases. The relevant git tag will have to be looked up instead.
