# Department Intelligence Agent

Collects news items from an RSS feed, uses Google Gemini to summarise and categorise them, and sends email briefings to different department audiences.

## At a glance

- **Input:** News items from the configured RSS source, collected on a schedule.
- **Processing:** Fetch the feed, summarise and classify items, then route the results by category.
- **Output:** Email briefings for Software Development, Data Analytics, Content & Design, and Finance.
- **Tools:** n8n Schedule Trigger, HTTP Request/RSS source, Google Gemini, Gmail.

## Workflow outline

`Scheduled run → Fetch RSS feed → Summarise and categorise → Split by department → Send briefing emails`

The export includes a separate email node for each of the four categories. The summaries and routing decisions should be checked against the original articles before this is used as an internal briefing system.

## Configuration

1. Import `workflow.json` into n8n.
2. Connect Google Gemini and Gmail credentials.
3. Review the configured RSS URL, schedule, output parser, department categories, and the recipient address in each email node.
4. Replace example recipient addresses with approved team distribution lists.
5. Test with a small set of items and verify that summaries are relevant, source links are preserved where expected, and each message goes to the intended audience.

## Manual test checklist

- [ ] A normal feed run creates department-specific summaries.
- [ ] An empty feed does not produce misleading empty briefings.
- [ ] Malformed or unexpected model output is detected during testing.
- [ ] A mail delivery error appears in execution history.
- [ ] Each category is routed to the correct test recipient.

## Notes and limitations

- Summaries can omit context or make classification mistakes. Keep original article links available for verification.
- Review schedule and recipients before activating the workflow.
- Potential improvements: combine multiple feeds, let teams configure topics, and retain a history of briefing summaries.

**Related files:** [Architecture](./architecture.md)
