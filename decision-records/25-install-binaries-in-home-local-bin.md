# Install binaries in ~/.local/bin

## Context
PATH contention in workstations, servers and CI/CD systems alike, creates uncertainties around what version of a binary is being executed when they're used. For example: you install a company approved version of terraform in your CI/CD pipeline, but when you run `terraform -version`, it continues outputting the version string of the latest release. Resolving such conflicts can be expensive.

There is existing ambiguity around where binaries should be installed: `/bin`, `/usr/bin`, `/usr/local/bin`, `/usr/local/share`, `/opt`, `/opt/local`, `/opt/homebrew/opt`, among others.

Developers sometimes mess up their workstations bad enough that a complete re-installation of the OS is warranted (e.g. by replacing system python). This is usually expensive and causes downtime as equipment has to be shipped around.

## Decision
We will install binaries in `~/.local/bin` as described in [file-hierarchy(7)](https://www.freedesktop.org/software/systemd/man/file-hierarchy.html#Home%20Directory).

`~/.local/bin` will have the highest priority in PATH resolution.

## Consequences
Installations of new binaries by the user do not require su permissions, meaning scripts don't need to ask the user for their password.

There is no cross contamination of binaries between workstation users, ensuring simpler workstation cleanup when refreshing equipment for the next user.

Developer workstations can be easily fixed up remotely by re-creating the user.

Sysadmins can expose required, sometimes licensed binaries, to only specific users on a given workstation.

Developers do not require write access to `/`, `/usr/*`, etc.

Binary locations are consistent regardless of the OS as `~/.local/bin` is an OS-neutral directory.
