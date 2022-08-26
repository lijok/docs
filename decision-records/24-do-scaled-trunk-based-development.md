# Do scaled trunk-based development

## Context
Git supports many workflows, each with their own pros and cons. This causes endless, usually fruitless debates within teams on what workflow is best suited for that team.

Git flow, a complex, widely popular git workflow, gives semantic meaning to branches and accommodates complex release workflows.

[Scaled trunk-based development](https://trunkbaseddevelopment.com/#scaled-trunk-based-development) is the simplest git workflow that does not compromise the stability of the master branch, scales with team size, allows to easily undo and hotfix mistakes, and does not create cognitive overhead for the team.

Releases can be automated by triggering CI/CD builds off of a git tag, or a push to master.

## Decision
We will do [scaled trunk-based development](https://trunkbaseddevelopment.com/#scaled-trunk-based-development).

## Consequences
Trunk-based development may be difficult to adjust to for people used to git flow.

Supporting multiple versions of a project with trunk-based development may become burdensome. If supporting multiple versions is absolutely required, and trunk-based development is causing issues, a project-specific decision record to use a different workflow (e.g. git flow) will have to be created to override this decision.
