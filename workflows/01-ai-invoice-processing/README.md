# AI Invoice Processing

I made this n8n workflow to explore how AI can help with the repetitive parts of invoice processing. It takes a PDF invoice, extracts the main details with Google Gemini, and sends the result to Google Sheets.

The workflow is intended as a demo. Before using it, connect your own Google account and test it with sample invoices.

## What it does

- Takes a PDF from Google Drive or a form submission.
- Extracts details such as invoice number, vendor, date, tax, total, and currency.
- Checks whether required details are missing.
- Looks for a possible duplicate in Google Sheets.
- Saves the result and sends an email based on the outcome.
- Flags invoices that need someone to check them.

## How it works

`Invoice PDF → Check file → Extract text → Gemini → Validate fields → Check duplicates → Google Sheets / email`

If the file is invalid or the extracted information needs checking, the workflow is intended to send it down a separate review or error path rather than treating it as a successful invoice.

## Tools used

- **n8n** — connects and runs the steps
- **Google Gemini** — extracts invoice details
- **Google Drive** — invoice files
- **Google Sheets** — stores results and helps check duplicates
- **Gmail** — sends notifications

## Data extracted

| Field | Required |
|---|---|
| Invoice number | Yes |
| Vendor name | Yes |
| Invoice date | Yes |
| Total amount | Yes |
| Tax amount | Yes |
| Currency | Yes |
| Line items and quantity | Optional |

## Before you run it

1. Import the workflow into your n8n instance.
2. Connect Google Drive, Google Sheets, Gmail, and Gemini credentials.
3. Update the folder, form, and sheet settings to match your own setup.
4. Use sample PDFs first and check the extracted values against the original invoice.

Workflow exports should not contain your personal API keys or credentials. Keep those in n8n's credential settings.

## Cases worth checking

Try a normal invoice, a PDF with a missing field, a duplicate invoice, a damaged PDF, and a non-PDF file. Check that each case ends up in the right place.

## Ideas for later

- Improve extraction from scanned invoices with OCR.
- Check vendor details against a separate vendor list.
- Add an approval step before an invoice is processed further.
