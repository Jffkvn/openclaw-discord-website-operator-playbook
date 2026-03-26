# Lessons Learned

## 1. Prompting Was Not The Main Problem

The early failures looked like model quality problems, but the deeper issue was runtime reliability. A bot with unclear execution rights becomes chatty, evasive, or misleading even when the prompt sounds strong.

## 2. Exactness Matters More Than Helpfulness

The most important rule that emerged from this build was simple:

- do the exact task, or
- say immediately that you cannot

Anything in between wastes time and reduces trust.

## 3. Scheduling Belongs In Durable Automation

Live chat is great for instructions and approvals. It is a poor place to store durable timing logic. Recurring jobs and delayed publishes belong in cron or another proper scheduler.

## 4. Narrow Write Surfaces Reduce Damage

Bots become safer when normal workflows touch fewer files. A narrow publishing surface is more sustainable than giving the operator broad freedom and hoping prompts will keep it careful.

## 5. Verification Changes The Whole Experience

The operator became much more trustworthy once it consistently:

- ran the build
- checked the result
- reported route counts or success evidence
- stopped claiming completion without proof

## 6. Browser Automation Is Useful But Fragile

Browser access helps, but UI automation is not the best backbone for critical repeatable tasks. Direct filesystem and CLI workflows are more stable for production work.

## 7. Public Sharing Requires A Redaction Mindset

A useful repo is not a raw dump. The value comes from:

- preserving the architecture
- preserving the debugging journey
- preserving the workflow logic

while stripping out:

- secrets
- identities
- client details
- machine-specific risk
