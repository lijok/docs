# Store documentation in Git

## Context
Documentation is rarely read and rots as soon as it is written. This is a universally understood fact in engineering teams.

Documentation rot sets in because the team members that write it over time learn enough context, that documentation and reference manuals become unnecessary for them. As that happens, maintaining documentation that is no longer required for those team members to do their function, becomes a mindless chore. Because documentation is often not stored next to the work it is documenting, it is infeasible to enforce that changes to work artefacts are presented together with documentation changes.

When documentation is stored in systems such as Confluence, peer review is infeasible. This results in documentation that is in some cases incorrect right from the first edition.

By storing documentation local to the work it is documenting, in a version controlled system such as git, with attached workflows that support peer review, we can alleviate some of these issues and prevent documentation rot.

## Decision
We will store all documentation in Git.

Project documentation will be stored in that projects repository under `docs`. All other documentation will be stored in the `documentation` repository.

## Consequences
Code and documentation can be updated in a single change, and corresponding processes can be developed to enforce that.

Scripts can be stored alongside generic documentation, which allows for leaner documentation as rather than documenting execution steps, a script can be supplied, together with very short documentation.

A GUI is required for team members outside of engineering to write and modify decision records.

Documenting higher level view of microservices has to be done in the `documentation` repo, if the codebases of said microservices are separate.
