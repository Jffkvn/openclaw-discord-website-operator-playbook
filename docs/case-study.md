# Case Study

## Goal

Build a local operator that could take instructions in Discord, update a website project safely on the same Mac, verify the build, and deploy only through a controlled publishing path.

## Starting Constraints

- The operator needed to work through Discord because that was the most practical operating surface.
- The publishing flow needed hard guardrails so the bot would not improvise changes across the whole codebase.
- The setup had to be practical, not theoretical. It had to run against a real website workflow.
- The operator needed to behave honestly: do the exact task, or say it could not.

## Early Failures

The first version had the worst possible combination:

- not autonomous enough to finish work smoothly
- confident enough to sound like it already had

That showed up as:

- fake progress language
- tool requests bouncing back to the user
- confusing approval failures
- inconsistent Discord-triggered shell access
- fragile browser-driven behavior

## Root Cause

The main lesson was that this was not just a prompting problem.

Part of the pain came from runtime behavior:

- a broken approval and exec path on an older OpenClaw version
- mismatches between what the agent appeared to be allowed to do and what the gateway actually let it do
- scheduling responsibilities living partly in chat instead of durable automation

Once that became clear, the work shifted from "keep patching prompts" to "stabilize the operator stack."

## What Changed

The system became reliable after three kinds of changes:

### 1. Runtime upgrade

Upgrading OpenClaw to a newer release resolved the most frustrating Discord-triggered exec failures and made local website work possible from the channel again.

### 2. Narrowed publishing surface

Instead of letting the bot roam widely, the website workflow was constrained to:

- local image preparation
- a single article-data file
- build verification
- a dedicated deploy script

That reduced the chance of toolchain damage during normal publishing work.

### 3. Better workflow boundaries

The responsibilities were split more cleanly:

- Discord for decisions, approvals, and status
- OpenClaw runtime for tool execution
- cron for recurring research and timed publishing

That made the system feel more like an operator and less like an unreliable chat assistant.

## Final Working Outcome

The final workflow reached a point where it could:

- receive publishing instructions in Discord
- inspect the local website project
- prepare article updates inside the guarded workflow
- run build verification and prerender checks
- deploy through the intended production path
- report success or failure back to Discord

It also supported a recurring content rhythm:

- Tuesday: research and shortlist ideas
- later in the week: publish approved articles on schedule

## Why This Matters

The useful lesson is not just that an AI tool can update a website.

The more important lesson is that operator systems fail when:

- runtime rules are unclear
- scheduling is improvised
- the model is rewarded for sounding helpful instead of being exact

This playbook exists to show how those issues were identified and reduced in a real setup.
