# OpenClaw Discord Website Operator Playbook

An anonymized, Mac-first playbook for building a reliable OpenClaw website operator that works through Discord, uses cron for scheduling, and safely updates production websites.

## What You Build

By the end of this repo, you should have a working operator that can:

- receive website-update instructions from Discord
- inspect and edit a local website project on the same Mac
- run build verification before claiming success
- deploy through a guarded publish script instead of ad hoc commands
- use cron for recurring research and timed publishing jobs

This is not a generic "AI bot" guide. It is specifically about building a Discord-driven website operator with strong workflow boundaries.

## Who This Is For

This repo is for builders who want to recreate a practical local operator workflow on macOS and care about:

- real tool execution
- safer publishing workflows
- repeatable scheduling
- reducing fake progress and vague agent behavior

## What This Repo Covers

This repo documents a real operator workflow that was built and debugged on macOS. The operator is designed to:

- receive work through Discord
- inspect and update a website project locally
- run build verification before claiming success
- deploy to production through a guarded publish script
- use cron for recurring planning and timed publishing

This is both:

- a case study showing the failures, constraints, and fixes
- a playbook that helps other builders recreate a similar setup on macOS

## Start Here

If your goal is to rebuild the setup, use this order:

1. [Recreate Checklist](./docs/recreate-checklist.md)
2. [Mac Setup](./docs/mac-setup.md)
3. [OpenClaw Setup](./docs/openclaw-setup.md)
4. [Discord Setup](./docs/discord-setup.md)
5. [Scheduling and Cron](./docs/scheduling-and-cron.md)
6. [Security and Redaction](./docs/security-and-redaction.md)

Then come back to:

- [Case Study](./docs/case-study.md)
- [Lessons Learned](./docs/lessons-learned.md)

## What Is Anonymized

The public version keeps the operator pattern and the lessons, but removes:

- client and project identities
- production domains
- real Discord or Telegram identifiers
- tokens, API keys, OAuth values, and auth profiles
- private screenshots and raw transcripts
- personal machine paths and unnecessary deploy details

## Why This Exists

The original setup was not reliable at first. The operator looked capable on paper, but in practice it had problems with:

- tool execution from Discord
- approval and runtime behavior
- overly chatty or misleading responses
- scheduling responsibilities being split across the wrong layers

The system became useful only after the runtime was stabilized, the publishing workflow was narrowed, and the scheduling model was cleaned up.

## What You Will Learn

- how to think about Discord as an operator surface rather than just a chat channel
- how to structure a guarded website publishing workflow
- where cron should own scheduling instead of live chat sessions
- how to reduce the difference between "sounds helpful" and "actually works"
- how to sanitize a real setup before sharing it publicly

## Quick Recreate Path

If you want the shortest version, the practical path is:

1. install Node, OpenClaw, and `webp` on macOS
2. create your local OpenClaw config from the example files
3. set up a Discord bot and connect it to OpenClaw
4. define a narrow website publishing workflow
5. prove the operator can reply, read files, run a build, and report the result
6. add a recurring shortlist cron job
7. add timed publish jobs only after the interactive flow works

## Architecture At A Glance

```mermaid
flowchart TD
  A["Discord channel"] --> B["OpenClaw operator"]
  B --> C["Local website project"]
  B --> D["Build verification"]
  D --> E["Deploy script"]
  F["Cron jobs"] --> B
  B --> G["Status and failure alerts"]
```

## Reading Order

1. [Recreate Checklist](./docs/recreate-checklist.md)
2. [Mac Setup](./docs/mac-setup.md)
3. [OpenClaw Setup](./docs/openclaw-setup.md)
4. [Discord Setup](./docs/discord-setup.md)
5. [Scheduling and Cron](./docs/scheduling-and-cron.md)
6. [Architecture](./docs/architecture.md)
7. [Case Study](./docs/case-study.md)
8. [Security and Redaction](./docs/security-and-redaction.md)
9. [Lessons Learned](./docs/lessons-learned.md)

## Repo Map

- [`docs/`](./docs)
  - recreate checklist, narrative, architecture, setup, security, and lessons
- [`sanitized-config/`](./sanitized-config)
  - example configuration files with placeholders only
- [`prompts/`](./prompts)
  - reusable prompt patterns for research, drafting, image prompting, publishing, and cleanup
- [`templates/`](./templates)
  - payload, approval, publish, and incident templates
- [`artifacts/`](./artifacts)
  - sanitized supporting evidence

## Security Note

This repo is meant to be reproducible, but not reckless. It intentionally omits the private values required to run a production setup. Read [Security and Redaction](./docs/security-and-redaction.md) before copying any pattern into a live environment.

## What This Repo Does Not Include

To keep the playbook public and safe, it does not include:

- real tokens or auth state
- raw production transcripts
- private client repositories
- real production domains or channel identifiers
- a guarantee that every model/provider combination will behave the same in your environment

## Current Status

This public version focuses on the macOS path. Future iterations may add broader cross-platform notes, but the validated setup described here is Mac-first by design.
