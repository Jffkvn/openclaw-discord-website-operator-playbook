# Remove Article Prompt

Completely remove the named article from the website workflow.

Rules:

- remove the article entry from the allowed article data file
- remove the local `.webp` asset if it belongs only to that article
- run build verification
- report whether prerender completed and include the route count
- do not deploy unless explicitly asked
