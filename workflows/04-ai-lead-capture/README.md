# AI Lead Capture

This workflow handles a new enquiry from a form. It saves the details in Google Sheets, uses Gemini to draft a welcome email, sends the email through Gmail, and notifies the team in Slack.

The point is to keep the first follow-up from getting missed when someone fills out a form.

## How it works

`Form submission → Save lead → Draft email with Gemini → Send email → Notify team in Slack`

## Tools used

- **n8n** — runs the workflow
- **Google Forms or n8n Form** — collects the enquiry
- **Google Sheets** — stores the lead details
- **Google Gemini** — drafts the welcome email
- **Gmail** — sends the email
- **Slack** — notifies the team

## Information collected

The form asks for the person's name, email address, and message. The workflow saves those details and uses the message to make the email more relevant.

## Before you run it

1. Import the workflow into n8n.
2. Connect your Google, Gemini, and Slack accounts.
3. Check the form fields and the Google Sheet columns.
4. Send a test enquiry using an email address you can access.
5. Check the email and Slack notification before using the workflow with real enquiries.

Use a fallback email if you want the workflow to continue when AI text generation fails. Keep credentials and personal information out of the exported workflow.

## Cases worth checking

Try a normal enquiry, an invalid email address, an AI request that fails, and a Google Sheets or email step that can't complete. Make sure failures are visible rather than silently losing the enquiry.

## Ideas for later

- Add lead categories based on the message.
- Connect the workflow to a CRM.
- Add a follow-up reminder if the lead has not received a response.
