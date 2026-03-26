# Recreate Checklist

Use this if your goal is to rebuild the workflow, not just read the story.

## Outcome

At the end of this checklist, you should have:

- OpenClaw running locally on macOS
- a Discord bot connected to your operator
- a local website project the operator can safely manage
- a guarded publish workflow with build verification
- cron jobs for weekly research and timed publishes

## Step 1: Prepare the Mac

- install Homebrew if needed
- install Node.js
- install the `webp` tools so `cwebp` is available
- install OpenClaw globally
- confirm `openclaw --version` works

Read: [Mac Setup](./mac-setup.md)

## Step 2: Create Local OpenClaw Config

- copy the example files from [`../sanitized-config/`](../sanitized-config)
- create your real local config under `~/.openclaw`
- add your own Discord token and any model/API credentials you plan to use

Read: [OpenClaw Setup](./openclaw-setup.md)

## Step 3: Connect Discord

- create a Discord application and bot
- enable the message-reading capabilities your workflow requires
- invite the bot to your server
- confirm the bot can reply in the chosen operator channel

Read: [Discord Setup](./discord-setup.md)

## Step 4: Define The Website Workflow

Before letting the operator touch a real site, define:

- which files it is allowed to edit
- how images should be prepared
- how builds should be verified
- which deploy script it must use

Do not skip this step. The narrower the workflow, the safer the operator becomes.

## Step 5: Run The Acceptance Test

In Discord, verify the operator can do these in order:

1. reply in the channel
2. read the website project
3. run the build command
4. report the real build result
5. publish through the guarded path only

If it cannot pass those tests, do not move on to automation yet.

## Step 6: Add Scheduling

Once the interactive flow works:

- add a recurring weekly research job
- add timed publish jobs
- add failure alerts

Read: [Scheduling and Cron](./scheduling-and-cron.md)

## Step 7: Review Public Safety

If you plan to share your setup or write about it publicly:

- strip secrets
- strip client identifiers
- strip private paths and IDs
- use redacted examples only

Read: [Security and Redaction](./security-and-redaction.md)

## Recommended Reading After Setup

- [Architecture](./architecture.md)
- [Case Study](./case-study.md)
- [Lessons Learned](./lessons-learned.md)
