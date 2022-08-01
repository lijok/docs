# Do not automate code coverage

## Context
Code coverage is considered to be a proxy metric for software quality and the ability to find issues before they hit production. Unfortunately, code coverage does not improve development practices, and in some cases, damages them, since Goodharts law applies.

Code coverage works great as a non-enforceable metric for tracking infrequent efforts such as getting a legacy system under test. It also works well as an audit tool to strategize where to concentrate testing efforts, and what code-paths are stale and can be removed.

Business interests may need to infrequently see code coverage statistics for compliance purposes.

## Decision
We will not use code coverage tools as part of automated workflows. We may, infrequently, utilize a code coverage tool manually as an audit mechanism to strategize where to concentrate our testing efforts.

## Consequences
Test quality, and coverage has to be enforced through peer review.

Code coverage metrics have to be collected manually and presented to the business on demand.
