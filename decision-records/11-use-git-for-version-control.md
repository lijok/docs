# Use Git for version control

## Context
Most work artefacts, such as code and documentation must be kept in a distributed version control system to enable collaboration, auditing, disaster recovery, etc.

Git is the most widely used version control system, and in turn, has the largest candidate pool for recruiting.

## Decision
We will use Git for version control.

## Consequences
Git does not deal well with large files, so LFS has to be used for large asset storage.
