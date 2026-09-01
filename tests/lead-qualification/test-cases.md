# Lead Qualification Tests

## Test Cases

| Test ID | Test Case | Input | Expected Result | Status |
|---------|-----------|-------|-----------------|--------|
| LQ-001 | Valid lead with phone | Pending status, valid phone | Call initiated | Manual |
| LQ-002 | Empty phone | No phone number | Skip lead | Manual |
| LQ-003 | Completed status | Status = Completed | Skip lead | Manual |
| LQ-004 | International phone | +91 prefix needed | Formatted correctly | Manual |
| LQ-005 | Call answered | Lead picks up | Webhook fires with transcript | Manual |
| LQ-006 | Call missed | No answer | No webhook, retry logic | Manual |
| LQ-007 | Vapi API down | Service unavailable | Error notification | Manual |

## Test Scenarios

### Happy Path
1. Lead with Pending status
2. Valid phone number
3. Call initiated
4. Lead answers
5. AI has conversation
6. Call ends
7. Webhook updates sheet

### Edge Cases
1. Voicemail
2. Wrong number
3. Lead interrupts
4. Long conversation
5. Multiple leads in batch
