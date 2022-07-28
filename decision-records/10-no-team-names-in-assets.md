# No team names in assets

## Context
Teams are a transient organizational structure. Code and other assets last much longer.

Injecting team names (e.g. `0-operations-database.sqlite`) into assets, or code, results in confusion and technical debt as soon as the team is disbanded.

Moving projects between teams becomes an unnecessarily complex exercise when team names are embedded in things like code, urls, filenames, etc.

## Decision
We will not embed team names in any assets, unless the assets disappear together with the team on disbanding (i.e. Slack channels).

## Consequences
Transferring asset ownership between teams (e.g. projects), becomes easier.
