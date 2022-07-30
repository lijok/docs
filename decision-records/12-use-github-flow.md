# Use GitHub flow

## Context
Git supports many workflows, each with their own pros and cons. This causes endless, usually fruitless debates within teams on what workflow is best suited for that team.

Git flow, a complex, widely known git workflow, gives semantic meaning to branches and accommodates complex release workflows.

GitHub flow is a name given to a simple workflow that dictates to create short-lived feature branches off of master, then merge them back into master through a pull request when work on the branch is done.

GitHub flow is the simplest git workflow that does not compromise the stability of the master branch, scales with team size, allows to easily undo and hotfix mistakes, and does not create cognitive overhead for the team.

Releases can be automated by triggering CI/CD builds off of a git tag, or a push to master.

## Decision
We will use GitHub flow.

## Consequences
Automation will be required to achieve painless releases.
