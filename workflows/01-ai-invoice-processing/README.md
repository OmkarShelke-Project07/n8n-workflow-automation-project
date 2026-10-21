# AI Invoice Processing

Extracts key fields from invoice PDFs, checks the extracted data, and records the result in Google Sheets. The workflow demonstrates how an AI extraction step can fit into a controlled document-processing process.

## At a glance

- **Input:** PDF invoice received through the configured Google Drive trigger or n8n form.
- **Processing:** Extract PDF text, use Google Gemini to structure invoice fields, validate required data, and check for a possible duplicate.
- **Output:** A spreadsheet record and an email notification or manual-review path, depending on the result.
- **Tools:** n8n, Google Gemini, Google Drive, Google Sheets, Gmail.

## Workflow outline

`Invoice PDF → File validation → PDF text extraction → Gemini extraction → Required-field checks → Duplicate check → Save / review / notify`

The workflow includes error paths for unreadable files, AI extraction failures, storage errors, invalid files, and duplicate candidates. Review the original invoice before relying on extracted amounts or tax values.

## Data fields

| Field | Purpose |
|---|---|
| Invoice number | Identify the invoice and support duplicate checks |
| Vendor name | Identify the supplier |
| Invoice date | Record the invoice date |
| Total amount, tax amount, currency | Capture the main financial values |
| Line items and quantity | Supporting invoice details when available |
| Status and processing timestamp | Track the workflow result |

## Configuration

1. Import `workflow.json` into your n8n instance.
2. Reconnect Google Drive, Google Sheets, Gmail, and Google Gemini credentials in the relevant nodes.
3. Replace `YOUR_INVOICE_SHEET_ID` / `YOUR_GOOGLE_SHEET_ID` and `YOUR_GOOGLE_DRIVE_FOLDER_ID` with your own resource IDs. Confirm the sheet tab and column names match the node mappings.
4. Review the form fields, file-type conditions, recipient email addresses, and notification messages.
5. Start with sample invoices and inspect each node's output before activating the workflow.

## Manual test checklist

- [ ] A readable PDF contains the expected invoice fields.
- [ ] A PDF with missing required information is sent for review.
- [ ] A duplicate invoice is identified using the configured matching fields.
- [ ] An invalid or unreadable file follows the error path.
- [ ] A Google Sheets or model error is visible and does not appear to be a successful processing result.

## Notes and limitations

- AI extraction can be wrong; compare totals, tax, vendor, and invoice number against the original file.
- The workflow export is inactive and requires your own credentials and IDs.
- Possible next improvements: OCR for image-only PDFs, vendor-master validation, and human approval before downstream accounting actions.

**Related files:** [Architecture](./architecture.md) · [Test cases](../../tests/invoice-processing/test-cases.md)
