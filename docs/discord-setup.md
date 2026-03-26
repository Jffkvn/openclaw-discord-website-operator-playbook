# Discord Setup

## Purpose

Discord acts as the operator console. It is where instructions, approvals, status messages, and failure alerts appear.

## Bot Setup Checklist

- create a Discord application
- add a bot user
- enable the intents your workflow actually needs
- invite the bot to the target server with the right permissions
- decide whether server channels, DMs, or both are part of the operator flow

## Suggested Setup Flow

### 1. Create the application and bot

- open the Discord Developer Portal
- create a new application
- add a bot user
- copy the bot token into your local `.env` file

### 2. Enable the right intents

Turn on the intents required for your workflow, especially if you want the operator to respond to normal channel messages rather than mentions only.

### 3. Invite the bot to your server

Give it only the permissions it actually needs for the operator workflow:

- read messages
- send messages
- embed links if you want richer confirmations
- read message content if your server workflow depends on it

### 4. Pair the user and channel

Once OpenClaw is connected, pair your account and confirm the bot can:

- reply in the chosen channel
- receive direct instructions
- send back build and publish confirmations

## Practical Permissions

For a website operator workflow, the bot typically needs to:

- read messages
- send messages
- read message content if channel commands depend on plain text
- post confirmations and alerts back into the chosen channel

## Channel Strategy

Treat Discord as:

- the planning and approval surface
- the publish notification surface

Do not rely on Discord alone to be the scheduler.

## Operational Advice

- use one channel for operator work instead of spreading state across many places
- keep prompts clear and task-shaped
- require the operator to report build verification before it claims success
- keep alerts in the same place where approvals happen

## What To Test First

Before trusting publishing work, test the channel in this order:

1. simple reply in the channel
2. local file read task
3. local build command
4. publish confirmation path

If the operator cannot pass those basic checks, do not move to live deployment yet.

## Example Acceptance-Test Prompt Sequence

These are the kinds of prompts worth testing first:

1. a simple channel greeting
2. "read this project and tell me the key article IDs"
3. "run the website build and tell me whether it passed"
4. "prepare the article update and show me the diff only"

The point is to prove execution, not just conversation.
