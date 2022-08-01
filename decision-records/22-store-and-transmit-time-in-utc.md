# Store and transmit time in UTC

## Context
Timezones, together with daylight savings time are universally understood to be difficult to handle, and are a major source of bugs in many systems that keep time.

UTC is a stable candidate for a fleet-wide time keeping standard.

UTC has very good timezone translation support.

## Decision
We will store and transmit timestamps in [Coordinated Universal Time](https://en.wikipedia.org/wiki/Coordinated_Universal_Time).

We will always store and transmit an explicit offset of Z (UTC) when a time component is present.

When presenting timestamps on user interfaces, we will adjust them for local timezone.

We will set hardware and OS clocks on servers to UTC.

## Consequences
Timestamps are guaranteed to be consistent for time in the past, even when timezones get changed or DST is applied.

[When storing future timestamps, such as upcoming event dates, UTC fails in the presence of timezone changes](https://codeblog.jonskeet.uk/2019/03/27/storing-utc-is-not-a-silver-bullet). This is because a user at +02:00 UTC might create an event date for 2022-09-01 14:00:00, which we would store as 2022-09-01T12:00:00+00:00. If then the timezone used by that country changes to +03:00 UTC, when displaying the date of the event, it will be 2022-09-01 15:00:00, which is 1 hour ahead of the intended time. For projects that must store such future dates (e.g. event organizer app, calendar app), a project-specific decision record will be required to override this decision record.
