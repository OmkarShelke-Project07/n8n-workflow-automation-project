# AI Lead Qualification

This workflow connects n8n with Vapi so a lead can be contacted by an AI voice assistant, and the call result can be saved back to Google Sheets.

I built it as a demo of connecting a phone call to the rest of a lead follow-up process. It still needs your own credentials and phone setup before it can be run.

## What it does

- Reads lead details from Google Sheets.
- Checks the lead's current status and phone number.
- Starts a call through Vapi when the row is ready.
- Receives the call update through a webhook.
- Saves the call status and available details back to the sheet.

The idea is to keep the call outcome with the lead record so someone can review it and decide what to do next.

## How it works

`Google Sheets → Check status and phone → Vapi call → Webhook → Read call result → Update sheet`

## Tools used

- **n8n** — runs the workflow
- **Vapi** — handles the voice call
- **Google Sheets** — stores lead details and call results
- **Webhook** — receives the call completion event
- **Google Gemini** — available for conversation analysis where configured

## Input and output

The input is a sheet row with lead details, including a phone number and current status.

The workflow can write details such as the call outcome, summary, transcript, call ID, and status back to the sheet, depending on what the call event returns.

## Before you run it

1. Import the workflow into n8n.
2. Add your Vapi and Google Sheets credentials.
3. Check the phone-number format and configure the assistant in Vapi.
4. Set up the webhook URL and make sure Vapi can reach it.
5. Test with a number you control before using any real leads.

Only call people who have agreed to be contacted, and follow the phone, privacy, and consent rules that apply to your use case. Don't put real lead data or API keys in the workflow export.

## Cases worth checking

Try a lead with a valid number, a missing number, a row already marked completed, and a call that doesn't complete. Confirm the sheet status makes sense in each case.

## Ideas for later

- Add a clear lead-scoring rule.
- Handle missed or failed calls with a retry path.
- Connect the results to a CRM or meeting calendar.
