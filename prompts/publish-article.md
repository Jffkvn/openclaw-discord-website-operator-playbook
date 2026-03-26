# Publish Article Prompt

Use the approved article and local image path to publish through the guarded website workflow.

Rules:

- convert the local image to `.webp`
- edit only the allowed website files
- run build verification before claiming success
- deploy through the approved publish script
- send a confirmation message with build status and production URL

If publish fails:

- send an alert immediately
- continue alerting on the agreed cadence until resolved
