# Mac Setup

## Assumptions

This playbook is written for macOS. It assumes:

- a local OpenClaw installation
- a working Node.js environment
- Homebrew available for system packages where needed
- Discord available on the same machine
- a local website project that the operator can access

## Baseline Install Path

Start from a clean terminal and install the core dependencies first.

### 1. Install Homebrew if needed

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2. Install the basic tools

```bash
brew install node webp
```

### 3. Install OpenClaw globally

```bash
npm install -g openclaw
```

### 4. Confirm the install

```bash
openclaw --version
openclaw gateway status
```

## Recommended Baseline

- macOS with Terminal access
- Node.js installed and consistent across the shell and the service runtime
- OpenClaw installed globally
- Google Chrome available if browser tooling is needed
- a dedicated working directory for the operator-managed website project

## Practical Advice

- keep the operator project and the target website project separate
- avoid mixing public playbook material with live `.openclaw` state
- prefer a managed browser profile rather than reusing your personal browsing state
- verify the service runtime after upgrades, especially if Node is managed through multiple tools

## Common Pitfall

If the service runtime points at one Node binary while the package was installed under another environment, debugging becomes much harder. Keep an eye on how the LaunchAgent or service command resolves Node and OpenClaw.

## Suggested Folder Layout

Keep the pieces separate:

- your live OpenClaw state in `~/.openclaw`
- your website project in its own dedicated project folder
- your public documentation repo in a completely different folder

That separation makes debugging and public sharing much safer.
