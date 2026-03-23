---

## `references/confluence-api-token.md`

```md
# Confluence API Token: Short Setup Guide

Use this when the user does not yet have a Confluence / Atlassian API token.

## For Confluence Cloud

1. Sign in to your Atlassian account.
2. Open Atlassian account security settings / API token management.
3. Click **Create API token**.
4. Give the token a clear label, for example:
   - `confluence-qa-orchestrator`
5. Copy the token and save it securely.
6. Provide the following to the skill:
   - Confluence base URL
   - Atlassian email
   - API token

## Notes
- The skill uses the Atlassian account email together with the API token.
- If your organization uses 2FA or SSO, API token authentication is still the normal way for REST API scripts.
- New Atlassian API tokens may have an expiration period, so if access stops working later, check token validity.

## What the user should send
- `CONFLUENCE_BASE_URL=...`
- `CONFLUENCE_EMAIL=...`
- `CONFLUENCE_API_TOKEN=...`