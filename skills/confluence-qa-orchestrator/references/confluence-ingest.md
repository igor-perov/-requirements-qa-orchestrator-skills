# Confluence Ingest Guidance

## Goal
Parse a Confluence space or subtree and extract requirement-bearing pages, then hand the result to `requirements-qa-orchestrator`.

## What to collect
For each page:
- page title
- page ID
- page URL
- parent page
- hierarchy level
- headings
- main body content
- tables
- bullet lists
- acceptance criteria
- notes indicating business rules
- role mentions
- environment references
- attachments or linked references if obviously relevant

## What to ignore when possible
- stale changelog notes
- generic meeting notes
- implementation-only technical notes with no requirement value
- decorative macros
- repetitive navigation content
- archived/deprecated sections unless explicitly marked as current scope

## User interaction flow
1. Connect to Confluence API.
2. Retrieve the page tree for the requested space or root.
3. Show the user a concise page tree.
4. Ask the user to select a root page/folder that contains the requirements if the root is still ambiguous.
5. Recursively fetch child pages from that root.
6. Continue downstream stages with `requirements-qa-orchestrator`.

## Output expectations
Create:
- `confluence-tree.md`
- `requirements-raw.json`

## Quality bar
The ingest phase should preserve structure and source references so that downstream artifacts can trace back to Confluence pages.
