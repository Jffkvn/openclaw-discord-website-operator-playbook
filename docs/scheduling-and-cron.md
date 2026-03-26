# Scheduling And Cron

## Why Cron Matters

A website operator needs durable timing. Chat sessions are useful for instructions and approvals, but recurring content research and timed publishes should live in cron.

## Working Pattern

The model described in this repo uses a weekly rhythm:

- Tuesday afternoon: research and shortlist
- later scheduled publishes: run on the chosen days and times

## Recommended Split

### Research job

A recurring job should:

- research a batch of practical article ideas
- shortlist the strongest options
- deliver them back to the Discord channel for human selection

Example schedule:

- Tuesday at 16:00 local time

### Publish jobs

Timed jobs should:

- use approved article content and image inputs
- update the website in the narrow allowed path
- run build verification
- deploy through the approved script
- send success confirmation

Example schedule:

- Wednesday morning for article 1
- Friday morning for article 2
- Monday morning for article 3

## Failure Alerts

If a publish fails, the system should:

- send an alert immediately
- repeat alerts on a fixed cadence until someone intervenes

This is better than silent failure and better than forcing the human to keep checking manually.

## Config Pattern

Use a recurring job for research and either:

- one-shot jobs for that week’s approved publishes, or
- a queue-driven recurring publish model if you want a more durable long-term system

## Future Improvement

One useful extension is a queue-based publishing system where:

- the approved weekly batch is stored once
- recurring publish jobs consume the next approved article automatically
- the jobs skip safely if the queue is empty or incomplete

That removes the need to keep creating ad hoc one-shot jobs every week.
