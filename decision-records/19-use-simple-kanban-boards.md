# Use simple Kanban boards

## Context
Over time, teams ease themselves into adding more and more columns to their Kanban boards and plugging in automation workflows, such as the ones supported by Jira, that trigger off of ticket movements on those Kanban boards. This is an overcomplicated bandaid that attempts to compensate for poor communication and lack of automated release workflows, which ends up slowing down the process and frustrating engineers.

In March 2022, Thoughtworks moved [Single team remote wall](https://www.thoughtworks.com/en-gb/radar/techniques/single-team-remote-wall) to their "adopt" stage.

## Decision
We will use simple Kanban boards.

We will have the following columns on our Kanban boards:
- Backlog
- Blocked
- In Progress
- Review
- Done

We will not integrate our Git hosting provider (e.g. GitHub), with our kanban boards.

## Consequences
Our Kanban boards are responsive and simple.
