# Use squash strategy for git merges

## Context
Git supports a few different merge strategies: rebase, merge, merge with fast forward (where possible), squash. Each has its own pros and cons. Rebase creates a beautiful linear history, but also rewrites it to achieve that. Merge retains the history, all commits, but pollutes the history with merge commits. Squashing creates a clean history with no merge commits, but discards commits during merge.

If each commit in a projects history can be built, mistakes can be easily reverted.

To maintain a clean git history, it is imperative that each commit is accompanied by a well written, succinct commit message. Unfortunately, most developers to not write good commit messages, as evidenced by looking at the commit history of almost any project.

To maintain a clean git history, it is also important that each commit is complete. If commit A makes a code change and commit B adds the test changes for the changes made in commit A, the history quickly becomes unreadable. Unfortunately, due to most developer work involving a lot of discovery, too many developers commit in such a fashion too often. When such commits show up in a pull request, it is often too late to fix, as fixing them is too complicated for most.

It therefore, takes a great developer, and a lot of cognitive load, to write clean, readable, complete commits.

Most developers write fairly good pull request messages, which are also easier to enforce. When squashing, on platforms like GitHub, pull request messages get embedded in the resulting commit message.

Pull requests containing more than one change, are easy to split into multiple pull requests.

## Decision
We will squash merges to master.

We may squash merges to other branches if so desired.

We will introduce one complete change per pull request.

## Consequences
Peer review must enforce the concept of one complete change per pull request.

If a developer submits a PR with more than one change, they have to re-raise multiple PRs instead.

Developers can write whatever commit messages they like to keep track of their work, so long as the pull request message is well written. This lowers a developers cognitive load, especially during discovery phase of development.

One complete change per pull request can be difficult for some developers to adjust to. This increases the cognitive load on developers who are not used to working in such a way.
