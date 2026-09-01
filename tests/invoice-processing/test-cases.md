# Invoice Processing Tests

## Test Cases

| Test ID | Test Case | Input | Expected Result | Status |
|---------|-----------|-------|-----------------|--------|
| INV-001 | Valid PDF invoice | Valid PDF with all fields | Processed successfully | Manual |
| INV-002 | Missing invoice number | PDF without invoice # | Manual review | Manual |
| INV-003 | Duplicate invoice | Existing invoice number | Skipped with notification | Manual |
| INV-004 | Corrupt PDF | Damaged PDF file | Error notification | Manual |
| INV-005 | Invalid AI response | PDF with unreadable content | Validation failure | Manual |
| INV-006 | Storage failure | Sheet API down | Error notification | Manual |
| INV-007 | Unsupported file | Non-PDF file | Rejected notification | Manual |
| INV-008 | Low confidence | Unclear invoice | Manual review | Manual |

## Test Scenarios

### Happy Path
1. Upload valid invoice PDF to Google Drive
2. Verify trigger fires
3. Verify AI extracts all fields
4. Verify data saved to Google Sheets
5. Verify success email sent

### Edge Cases
1. PDF with multiple pages
2. PDF with image-based content (OCR needed)
3. Very small invoices
4. Multi-currency invoices
5. Invoices with discount lines

## Performance Tests
- Processing time per invoice
- Concurrent invoice processing
- API rate limit handling
