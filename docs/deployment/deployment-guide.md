# Deployment and Import Guide

This repository stores n8n workflow JSON exports and documentation. It does **not** include a ready-to-run production server configuration, and copying the `workflows/` directory into a container does not automatically import those workflows.

For current installation and configuration options, use the [official n8n Docker documentation](https://docs.n8n.io/hosting/installation/docker/).

## Option 1: n8n Cloud

1. Create or open your n8n workspace.
2. Open the project folder in this repository and read its README.
3. Import the project's `workflow.json` using n8n's workflow import option.
4. Configure credentials, resource IDs, recipients, webhook callbacks, and any required environment variables.
5. Test with sample data and keep the workflow inactive until the result has been checked.

## Option 2: Self-hosted with Docker

Docker runs n8n in a container. For a persistent setup, use the official image and keep n8n's data directory in a persistent volume or another supported persistent storage configuration. Do not rely on a temporary container filesystem for important workflows or credentials.

A basic local learning setup is shown in the official guide. Before exposing a self-hosted instance to the internet:

- Configure HTTPS and the correct public webhook/base URL.
- Protect the editor with n8n's supported user-management and authentication features.
- Set and protect a stable n8n encryption key; keep it outside Git and back it up securely.
- Persist n8n data and schedule backups.
- Keep the n8n version updated and limit network access to the editor and webhook endpoints.
- Review execution-data retention and error monitoring for the data your workflows handle.

## Workflow import is separate from deployment

Importing a JSON file creates a workflow in n8n; it does not provision API accounts, configure OAuth consent, create Google Sheets, create Pinecone indexes, set Vapi call assistants, or grant social publishing permissions. Those integrations must be configured separately.

After import, reconnect the credentials that the export no longer contains. Replace every `YOUR_...` placeholder and review the relevant project README.

## Environment variables used by example workflows

Some HTTP Request nodes use expressions that read runtime variables:

- Lead qualification: `VAPI_ACCESS_TOKEN`, `VAPI_ASSISTANT_ID`, `VAPI_PHONE_NUMBER_ID`.
- Social content publishing: `FACEBOOK_PAGE_ID`, `FACEBOOK_ACCESS_TOKEN`.

Availability of environment variables in expressions depends on the n8n hosting configuration. If the expression cannot read a variable, use a supported credential-based configuration or configure the self-hosted runtime appropriately. Never place a real token directly into the JSON export.

See the [security practices](../security/security-practices.md) and [testing strategy](../testing/testing-strategy.md) before enabling a workflow.
