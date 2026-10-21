# AI Lead Qualification

Connects Google Sheets with Vapi to contact an eligible lead using an AI voice assistant and write the resulting call information back to a sheet.

## At a glance

- **Input:** Lead row with contact details, a phone number, and a status that allows calling.
- **Processing:** Check the row and phone number, send a call request to Vapi, then receive call updates through an n8n webhook.
- **Output:** Call status and the available call details recorded in Google Sheets, with qualified and not-qualified paths.
- **Tools:** n8n, Vapi, Google Sheets, HTTP Request, webhooks.

## Workflow outline

`Eligible lead in Sheets → Validate status and number → Vapi call request → Vapi event webhook → Interpret outcome → Update lead record`

The workflow includes a manual-start path for initiating eligible leads and a webhook path for call events. The exact fields available for a transcript or summary depend on the event payload returned by Vapi.

## Configuration

1. Import `workflow.json` into n8n and reconnect Google Sheets credentials.
2. Configure a test Google Sheet and replace the placeholder spreadsheet ID in all Sheets nodes. Confirm the sheet names and columns match the mapping.
3. Configure your Vapi assistant and phone number, then provide `VAPI_ACCESS_TOKEN`, `VAPI_ASSISTANT_ID`, and `VAPI_PHONE_NUMBER_ID` in the n8n runtime if environment expressions are supported. Otherwise, replace these expressions with an authentication method supported by your deployment.
4. Configure the webhook URL in Vapi to point to the production or test webhook URL shown by n8n. Test the callback before processing multiple leads.
5. Start with a phone number you control and verify the call request, callback, and sheet update.

## Manual test checklist

- [ ] A lead with a valid number and eligible status starts a call.
- [ ] A row with a missing or invalid phone number is not called.
- [ ] A lead already marked as completed is not accidentally called again.
- [ ] A completed, failed, or unanswered call is reflected accurately in the sheet.
- [ ] The webhook handles the event payload actually sent by Vapi.

## Consent and safety

Only contact people who have consented to receive calls. Follow the laws and platform rules that apply to your audience and location. Do not use real customer contact information in public examples or screenshots.

**Related files:** [Architecture](./architecture.md) · [Test cases](../../tests/lead-qualification/test-cases.md)
