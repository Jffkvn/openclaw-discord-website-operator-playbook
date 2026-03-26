# OpenClaw Setup

## Core Principle

The operator is only useful if the runtime, permissions, and workflow rules all agree with each other.

## What To Configure

At a high level, you need:

- a working model/provider path
- Discord channel integration
- browser access only if your workflow truly needs it
- command execution that actually matches your intended approval model
- a clear workflow document for what the operator is allowed to change

## Minimal Local Setup

### 1. Create your local config files

Use the examples in:

- [`../sanitized-config/openclaw.json.example`](../sanitized-config/openclaw.json.example)
- [`../sanitized-config/.env.example`](../sanitized-config/.env.example)

Copy them into your local OpenClaw state and replace placeholders with your own values.

### 2. Choose the model path

For this style of operator, test the model in the context that matters:

- can it stay concise?
- can it avoid fake progress?
- can it use tools reliably in your runtime?

Do not choose based on benchmarks alone.

### 3. Start the gateway

```bash
openclaw gateway status
```

If it is not running yet, start or reload it through the method your install uses.

### 4. Verify the runtime from the real operating surface

Do not stop at terminal checks. Confirm from Discord that the operator can:

- read the target project
- run a build
- report the real result

## Important Runtime Lesson

If the operator looks like it has permission but the gateway denies execution in practice, the user experience becomes confusing fast. Before blaming prompting, verify the actual runtime path:

- can it read the target project?
- can it run the needed build command?
- can it report the result back through Discord?

## Recommended Guardrails

- keep normal publishing inside a narrow file surface
- avoid asking the operator to improvise toolchain changes during routine publishing
- require build verification before success claims
- push recurring timing logic into cron rather than depending on live chat state

## Workflow File

Give the operator a clear workflow document for the website project it manages. The stronger the boundaries, the safer the day-to-day publishing flow becomes.

## Provider Advice

Choose the model path that balances:

- cost
- speed
- task honesty
- tool behavior

The best model on paper is not always the best operator in practice.
