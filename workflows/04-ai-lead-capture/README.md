# AI Lead Capture

Captures a new enquiry, stores the lead details, drafts a welcome email with Google Gemini, sends the email through Gmail, and notifies the team in Slack.

## At a glance

- **Input:** Form submission with the person's name, email address, and enquiry message.
- **Processing:** Save lead details, generate a draft tailored to the enquiry, and send notifications.
- **Output:** Lead record in Google Sheets, welcome email, and Slack notification.
- **Tools:** n8n form trigger, Google Gemini, Google Sheets, Gmail, Slack.

## Workflow outline

`New form submission → Save lead → Generate welcome message → Send email → Notify team`

Review the generated email before using this with live leads. Configure a safe fallback message or an error branch if the AI service is unavailable.

## Configuration

1. Import `workflow.json` into n8n.
2. Connect Google Gemini, Google Sheets, Gmail, and Slack credentials in n8n.
3. Replace the spreadsheet ID placeholder with your own ID. Confirm the sheet tab and column names match the workflow mapping.
4. Review the form field names, recipient address mappings, email wording, and Slack destination.
5. Submit a test enquiry using an inbox and Slack channel you control; confirm the lead is saved and that the right messages are sent.

## Manual test checklist

- [ ] A normal form submission is recorded with the expected fields.
- [ ] An invalid or missing email address is handled safely.
- [ ] An AI model failure does not silently discard a lead.
- [ ] A Sheets, Gmail, or Slack failure is visible in the execution history.
- [ ] Duplicate form submissions do not create unwanted duplicate follow-ups.

## Notes and limitations

- Generated text may be inaccurate or unsuitable; review message content and recipients.
- Keep personal information and credentials out of exports, source control, and public screenshots.
- Potential improvements: lead categorization, CRM integration, follow-up reminders, and deduplication by email.

**Related files:** [Architecture](./architecture.md)
