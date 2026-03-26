# Security And Redaction

## Public Sharing Rule

This repo should teach the workflow, not expose the live environment.

## Safe To Publish

- anonymized architecture
- generalized setup steps
- redacted configuration examples
- sanitized prompt patterns
- summarized logs
- blurred or cropped screenshots
- lessons learned

## Publish Only If Redacted

- config files
- job payloads
- screenshots from live channels
- build and deploy output
- LaunchAgent examples
- filesystem examples that could reveal identity or clients

## Never Publish

- `.env`
- API keys or tokens
- auth profiles
- raw session transcripts
- OAuth callback values
- private channel identifiers
- client names or domains when anonymization is required
- machine-specific paths that identify a real person or organization

## Screenshot Hygiene

Before publishing any image:

- crop hard
- blur usernames
- blur channel names if needed
- blur IDs, URLs, timestamps, and any sidebars that reveal extra context

## Path Hygiene

Replace private absolute paths with generic placeholders where possible. If you need to show a realistic example, make it obviously generic.

## Client Hygiene

If the playbook is based on a real client workflow:

- keep the workflow pattern
- remove the client identity
- remove unnecessary business details
- never publish private repository contents unless you own the right to do so
