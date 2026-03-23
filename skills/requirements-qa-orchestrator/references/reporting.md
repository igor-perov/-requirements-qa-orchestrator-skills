# Reporting Guidance

## Goal

Produce a stakeholder-ready report that quickly shows scope, quality, blockers, and defects.

## Required Outputs

- `execution-plan.md`
- `execution-results.md`
- `run-summary.json`
- `qa-report.html`
- `qa-report.pdf`

## HTML/PDF Quality Bar

The report should be visibly stronger than a raw dump. Prefer:

- a header with environment and run metadata
- summary cards
- a simple opening diagram or chart
- execution results table
- blocked section
- defect section
- evidence panels or screenshot references

## Defect and Blocker Handling

- blocked cases stay in a blocked section
- failed cases may become defect cards
- do not convert blocked cases into defects

For each defect include:

- title
- linked test case
- linked requirement ids
- steps executed
- failure description
- screenshot path if available

## PDF Rule

Export PDFs through `playwright-cli` and prefer landscape orientation for dashboard-style reports.

```bash
npm install -g @playwright/cli@latest
playwright-cli --help
playwright-cli install --skills
```

## Reader Outcome

A PM, BA, QA lead, or engineer should understand in under a minute:

- what was tested
- what passed
- what failed
- what was blocked
- what needs follow-up
