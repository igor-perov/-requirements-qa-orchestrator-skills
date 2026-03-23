# Requirements QA Orchestrator Skills

Shareable Codex skills for requirements-driven QA work.

This repo packages two skills:

- `requirements-qa-orchestrator`
  - the flagship workflow for turning requirements into test cases, execution subsets, browser validation, and stakeholder-ready reports
- `confluence-qa-orchestrator`
  - a compatibility wrapper for teams that want a Confluence-led entry point

## Repo Layout

```text
skills/
  requirements-qa-orchestrator/
  confluence-qa-orchestrator/
scripts/
  install_local_skills.py
  smoke_validate.py
```

## Dependencies

- Python 3.9+
- `npm` and `npx`
- Playwright CLI for browser execution and PDF export

You can use either a global install:

```bash
npm install -g @playwright/cli@latest
playwright-cli --help
playwright-cli install --skills
```

Or the bundled `npx` fallback built into the PDF export helper.

## Install Locally

Clone the repo, then install the packaged skills into your Codex skills directory:

```bash
python3 scripts/install_local_skills.py
```

To install only the flagship skill:

```bash
python3 scripts/install_local_skills.py --skill requirements-qa-orchestrator
```

To replace existing installed copies:

```bash
python3 scripts/install_local_skills.py --overwrite
```

Restart Codex after installing.

## Install From GitHub

After pushing this repo to GitHub, people can install directly with Codex's built-in installer.

In Codex, they can ask:

```text
Use $skill-installer to install requirements-qa-orchestrator and confluence-qa-orchestrator from <owner>/<repo>.
```

Or they can run the installer script directly from their local Codex setup:

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo <owner>/<repo> \
  --path skills/requirements-qa-orchestrator \
  --path skills/confluence-qa-orchestrator
```

Restart Codex after installing.

## Smoke Validation

Run the packaged skill test suite and build a sample HTML report:

```bash
python3 scripts/smoke_validate.py
```

Also verify PDF export:

```bash
python3 scripts/smoke_validate.py --with-pdf
```

## Example Starter Prompts

- "Pull requirements from Confluence and generate test cases"
- "Here is a PRD markdown file. Normalize it and create QA coverage"
- "Here is a requirements JSON file. Build traceable QA artifacts"
- "Here is a test-cases JSON file. Run the top 5 high-priority cases on staging"
- "Turn these execution results into an HTML and PDF stakeholder report"

## What This Repo Optimizes For

- lower token spend through script helpers and canonical JSON artifacts
- guided intake that asks only the next blocker question
- preserved `test-cases` generation rules
- `playwright-cli` browser execution and PDF export
- reusable installation for teams and projects
