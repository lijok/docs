# Record decisions

## Context
Decisions, be they business, architectural, or any other, are often tribal knowledge. When decisions do get documented, more often than not, they are buried within larger documents which lack information pertaining to that decision.

When decisions are not documented, or, documented in an inconsistent, difficult to discover manner, organizations suffer from the following problems, among others:
- Duplicate discussions with each new motivated team member, as they question why certain decisions have been made
- Lack of consistency among projects, as changes that go against a particular decision easily slip through the cracks
- Frustration among team members, as certain conventions, without a documented rationale, get perceived as dogma
- Loss in productivity as team members have to scour for information regarding how certain significant works should be implemented

## Decision
We will keep a collection of decision records for significant decisions.

A decision record is a short text file in a format similar to an Alexandrian pattern. Each record describes a set of forces and a single decision in response to those forces. Note that the decision is the central piece here, so specific forces may appear in multiple decision records.

We will keep global, cross-project decision records in the `documentation` repository, under the `decision-records` directory.

We will keep project-specific decision records in the project repository under `docs/decision-records`.

Decision records will be written in plain text, Markdown files.

Decision records will be kept in a version controlled system, such as `git`.

Decision records will be numbered sequentially and monotonically. Numbers will not be reused.

Decision record file names will contain the number of the decision record, and its title. e.g. `0-record-decisions.md`, `1-bug-bounty-reward-scheme-review-cadence.md`.

If a decision is deprecated, reversed, or superseded, we will move it to `docs/decision-records/deprecated`, marking it as deprecated.

We will use a format with just a few parts, so each document is easy to digest (this document is written in the format described below, and should be used as a template):
- Title
- Context
- Decision
- Consequences

Titles are short, to the point, and written as a call to action where possible. For example, `Use Mutual Auth for cross-system auth`, `No team names in asset identifiers`, etc. Some decisions may describe a specification, such as, what code style to use, or how often a bug bounty reward scheme should be reviewed. Titles of such decisions cannot always be expressed as a call to action. In such cases, the titles should indicate the type of specification, e.g. `Python Code Style`, `Bug bounty reward scheme review cadence`.

Context section describes the forces at play, including business, technological, political, social, and project local. These forces are probably in tension, and should be called out as such. The language in this section is value-neutral. It is simply describing facts.

Decision section describes our response to these forces. It is stated in full sentences, with active voice, e.g. `We will …`.

Consequences section describes the resulting context, after applying the decision. All consequences should be listed here, not just the "positive" ones. A particular decision may have positive, negative, and neutral consequences, but all of them affect the team and the project in the future.

While some implementations of decision records, or architectural decision records, also known as ADRs, include a "Status" section, we will omit it. As stated above, decision records must be kept in a version controlled system, such as git. Therefore, the presence of a decision record in `docs/decision-records` should indicate it to be a decision in play.

Proposed decision records may be kept in `docs/decision-records/proposed`, if the version controlled system being used to store them, does not support proposals.

The date, on which the record appeared in `docs/decision-records`, as dictated by the version control system, should be treated as the date of the decision entering play. The same applies to deprecated records being moved to `docs/decision-records/deprecated`.

Decision records should be as clear, terse and succinct as the author is capable of making them, while not omitting important details. Records can be revisited and their language updated to increase the quality of the decision record.

Whether a decision is significant enough to be recorded, is hard to answer. A decision can be understood to be significant if it has far-reaching consequences. Ultimately, the objective of recording decisions is to save time and reduce mistakes. So, whether something is significant enough or not to warrant a decision being formalized, depends on how much discussion or noise it generates.

## Consequences
New team members will be onboarded onto projects faster.

Duplicate discussions, and debates during peer reviews will be cut short by referring to decision records.

The consequences of one decision record are very likely to become the context for subsequent decision records. This is also similar to Alexander's idea of a pattern language: the large-scale responses create spaces for the smaller scale to fit into.

Project stakeholders can see the decisions, even as the team composition changes over time.

The motivation behind previous decisions is visible for everyone, present and future. Nobody is left scratching their heads to understand, "What were they thinking?" and the time to change old decisions will be clear from changes in the project's context.

A GUI will have be provided to team members outside of engineering to write and modify decision records.

Decisions can be read in the terminal.

Decisions will be formatted nicely and hyperlinked by the
browsers of project hosting sites like GitHub and Bitbucket.

Tools like [Pandoc](http://pandoc.org/) can be used to convert
the decision records into HTML or PDF.
