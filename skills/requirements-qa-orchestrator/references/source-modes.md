# Source Modes

## Goal

Support multiple start modes without forcing everything through Confluence.

## Supported Modes

### `confluence`

Use when requirements live in an Atlassian page tree or folder.

Required for ingest:
- base URL
- user email
- API token
- root page or folder id/url

Outputs:
- `confluence-tree.md`
- `requirements-raw.json`

### `requirements_json`

Use when normalized or semi-structured requirements already exist in JSON.

Required:
- input file path or pasted JSON

Preserve:
- source references
- requirement ids if stable
- acceptance criteria and business rules

Output:
- canonical `requirements-normalized.json`

### `test_cases_json`

Use when cases already exist and the task starts at execution or reporting.

Required:
- input file path or pasted JSON

Preserve:
- test case ids
- linked requirement ids
- priority
- preconditions, steps, expected results

Output:
- canonical `test-cases.json`

### `markdown`

Use for PRDs, specs, or markdown files.

Required:
- input file path

Output:
- `requirements-raw.json`

### `pasted_text`

Use when the user pastes requirement text directly in the chat.

Required:
- pasted content

Output:
- `requirements-raw.json`

## Canonical Import Rule

Normalize every non-canonical source into the internal artifact shapes before asking the model to do expensive reasoning.

## Skip Rules

- Skip Confluence questions if the source is JSON, markdown, or pasted text.
- Skip normalization if canonical normalized requirements already exist and the user wants execution or reporting.
- Skip case generation if test cases are already supplied.
