# Requirements Normalization Guidance

## Goal
Transform raw Confluence content into a clean, testable requirement package.

## Normalize into
For each meaningful requirement:
- stable requirement ID
- feature/module name
- source page title
- source page URL
- requirement statement
- acceptance criteria
- roles involved
- business rules
- dependencies
- assumptions or ambiguities

## Recommended format
Use sections like:
- Feature
- Requirement ID
- Source
- Description
- Acceptance Criteria
- Roles
- Validation Rules
- Edge Notes
- Assumptions
- Open Questions

## Rules
- merge duplicate requirement statements if they are clearly the same
- keep source links
- do not silently drop ambiguity
- explicitly mark unclear behavior
- separate implementation notes from product behavior
- convert scattered details into testable statements whenever possible

## Key outputs
- `project-summary.md`
- `requirements-normalized.md`
- `requirements-traceability.json`

## Quality bar
The normalized requirements should be understandable without reopening Confluence for every detail.