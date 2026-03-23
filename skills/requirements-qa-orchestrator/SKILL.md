---
name: requirements-qa-orchestrator
description: Use when requirements need to be turned into test cases, execution subsets, browser validation, or QA reports from Confluence, JSON, markdown, or pasted text.
---

# Requirements QA Orchestrator

## Overview

This is the flagship requirements-to-QA workflow.

It is prompt-first, but uses bundled scripts and canonical JSON artifacts to reduce token spend across intake, normalization, case generation, execution, and reporting.

## When to Use

- Requirements start in Confluence
- Requirements already exist as JSON
- A PRD or spec exists as markdown
- The user pastes requirements text directly
- The user only wants execution from existing test cases
- The user only wants a report from existing execution results

## Startup Contract

1. Infer the likely source mode and stage with `scripts/detect_start_mode.py`.
2. Always confirm:
   - what the user wants to produce
   - what the source input is
3. Ask only the next blocker question.
4. If the source and requested outcome are already clear, start immediately.

## Stage Model

- `ingest`
- `normalize`
- `generate-cases`
- `execute`
- `report`

Detailed rules live in:
- `references/intake-and-stage-inference.md`
- `references/source-modes.md`
- `references/execution-policy.md`
- `references/reporting.md`

## Hard Rules

- Confluence support stays first-class, but it is optional.
- When generating test cases, do not invent a new methodology.
- Use the bundled `references/embedded-test-cases-skill.md` guidance as the quality baseline.
- Use `scripts/prepare_test_case_brief.py` only to reduce token spend and shape inputs.
- Browser execution and PDF export must use `playwright-cli`.
- Prefer canonical JSON artifacts first, then render markdown and HTML from them.
- Keep reusable scripts and templates in this skill folder; create project-local files only for outputs and run artifacts.

## Primary Scripts

- `scripts/detect_start_mode.py`
- `scripts/ingest_confluence.py`
- `scripts/ingest_markdown.py`
- `scripts/import_requirements_json.py`
- `scripts/import_test_cases_json.py`
- `scripts/normalize_requirements.py`
- `scripts/prepare_test_case_brief.py`
- `scripts/select_execution_subset.py`
- `scripts/build_report_bundle.py`
- `scripts/export_report_pdf.py`

## Compatibility

Use `requirements-qa-orchestrator` for the general workflow.
Use `confluence-qa-orchestrator` only when the user is clearly starting from Confluence and wants the Confluence-led entry point.
