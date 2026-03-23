---
name: confluence-qa-orchestrator
description: Use when the request clearly starts from Confluence pages, folders, or spaces and needs a Confluence-led entry point into requirements-driven QA work.
---

# Confluence QA Orchestrator

## Overview

This skill is the Confluence-specialized entry point for the broader `requirements-qa-orchestrator` workflow.

Use it when the source of truth is a Confluence page tree, space, folder, or page URL and the first task is to pull requirement content from Atlassian.

## What This Wrapper Owns

- Confluence auth guidance
- root page or folder selection
- subtree ingest strategy
- source preservation for downstream traceability

## What It Does Not Own

After ingest, continue with the flagship workflow in `requirements-qa-orchestrator` for:

- stage inference
- normalization
- case generation
- execution subset selection
- browser execution with `playwright-cli`
- HTML/PDF reporting

## Hard Rules

- Keep Confluence-specific auth/setup help in this wrapper.
- Use the bundled Confluence ingest guidance and helper script for subtree extraction.
- Preserve source URLs and page titles.
- Keep the shared execution and case-generation anchors:
  - `requirements-qa-orchestrator`
  - embedded `test-cases` guidance
  - `playwright-cli`

## Default Flow

1. Confirm the Confluence source root.
2. Gather the smallest requirement-bearing subtree that matches the requested scope.
3. Export `confluence-tree.md` and `requirements-raw.json`.
4. Continue the rest of the workflow using `requirements-qa-orchestrator`.
