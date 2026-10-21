# Security Practices

This repository contains example workflow exports for learning and portfolio review. Treat exported workflows as code that must be reviewed before use.

## Credential handling

- Add Google, OpenAI, Pinecone, Vapi, Slack, LinkedIn, and other credentials through n8n's credential settings wherever the node supports it.
- A few HTTP Request nodes reference runtime environment variables. Those expressions work only when the n8n hosting configuration allows access to the named variables.
- Never paste real API keys, bearer tokens, refresh tokens, phone numbers, private customer data, or production webhook URLs into workflow JSON, README files, screenshots, or test fixtures.
- Keep populated `.env` files out of Git. The committed `.env.example` should contain names and setup guidance only, not working secrets.

## Public workflow exports

The workflow JSON files in this repository are sanitized examples. Saved n8n credential references and identified account-specific spreadsheet/Drive IDs have been removed or replaced with placeholders. After importing, you must reconnect credentials and replace placeholders with resources you control.

**Important: sanitizing the latest file does not erase old Git commits.** An earlier version of the social-content workflow contained a Facebook access token. Revoke/rotate that token in Facebook if it was real or could have been valid. Review repository history for other exposed values and rotate anything that may have been compromised. If the repository is shared, consider the appropriate history-cleanup process after revocation.

## Before sharing or deploying

- [ ] Search staged files and the full diff for access tokens, API keys, passwords, private email addresses, and customer data.
- [ ] Confirm every sheet, folder, social account, recipient, and webhook belongs to the intended test or production environment.
- [ ] Grant only the API permissions the workflow needs.
- [ ] Use test sheets and non-sensitive sample data first.
- [ ] Keep workflows inactive until their credentials, destinations, and error paths have been reviewed.
- [ ] Use HTTPS for externally reachable webhooks and deployment endpoints.
- [ ] Store backups securely and restrict access to n8n and its credential database.

## Automated checks

GitHub Actions checks JSON syntax, basic workflow structure, inactive status, README presence, and several common secret patterns. These checks are useful guardrails, but they are not a full secret scanner and cannot guarantee that every sensitive value has been detected. Review changes manually and consider running a dedicated secret scanner before publishing.

## Incident response

If a token or credential is exposed:

1. Revoke or rotate it at the service that issued it.
2. Check recent usage logs where available.
3. Replace the exposed value in active systems and repository files.
4. Review Git history and assess whether it needs cleanup.
5. Document the incident and improve the checks that missed it.
