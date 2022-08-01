# Asset identifiers

## Context
Case sensitivity is very common. We see it in Docker tags, linux file systems, simplistic search implementations, etc. Mixing uppercase and lowercase identifiers can cause issues such as:
- Terraform state migrations become very tricky
- Grafana queries have to know exact casing of identifiers
- Prior to doing file lookups, filenames have to be normalized
- Amazon support unable to locate your resource because the casing is wrong

## Decision
We will use lowercase, machine-readable identifiers, for all assets, where possible.

We will use kebab-case, where possible, as word separators. Where not possible (3rd party service with strict naming restriction), under_scores or camelCase may be used.

Where numbering is required, i.e. decision records, multiple instances of a database - numbering schemes will start at 0, without any padding (don't use something like 001).

## Consequences
Asset names remain consistent where allowed by our tool stack.

Inconsistencies are introduced when 3rd party software or services do not support kebab-case (e.g. some AWS services).
