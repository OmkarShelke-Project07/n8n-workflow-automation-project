# AI Content Generation

Generates social media copy from a topic and brief, requests an image from Pollinations.ai, publishes to configured LinkedIn and Facebook destinations, and logs post details to Google Sheets.

## At a glance

- **Input:** Topic, short brief, and tone (pre-filled in the example Set node).
- **Processing:** Generate platform-specific captions, hashtags, a call to action and image prompt; request an image; pass content to the connected publishing nodes.
- **Output:** A LinkedIn post, a Facebook post, and rows in the configured log sheet when the integrations succeed.
- **Tools:** n8n, Google Gemini, Pollinations.ai, LinkedIn, Facebook Graph API, Google Sheets.

The workflow also asks the model to generate Instagram caption copy, but the current export does **not** include an Instagram publishing node.

## Workflow outline

`Manual trigger → Set topic/brief/tone → Check required input → Gemini output → Image request → LinkedIn / Facebook → Log results`

The current export is a starting point, not a guarantee that publishing will work without editing. Verify the structured output schema and field mapping, the generated image response/binary handling, platform permissions, and the values written to the log sheet before enabling publishing.

## Configuration

1. Import `workflow.json` into n8n and reconnect Google Gemini, LinkedIn, and Google Sheets credentials.
2. Replace `YOUR_LINKEDIN_PERSON_ID` and `YOUR_SOCIAL_POST_LOG_SHEET_ID` with your own resource values.
3. Configure `FACEBOOK_PAGE_ID` and `FACEBOOK_ACCESS_TOKEN` as supported runtime environment variables, or replace those expressions with a supported credential-based authentication setup. Confirm the n8n environment allows the workflow to read those variables.
4. Review the Facebook Graph API endpoint/version, image URL or binary mapping, output parser schema, caption extraction expressions, and Sheet column names.
5. Use a test page/account and non-sensitive content. Verify the draft, image, post, and log before allowing public publishing.

## Manual test checklist

- [ ] Missing topic or brief stops the workflow with a clear error.
- [ ] Model output contains every field expected by the parser and caption expressions.
- [ ] The image request returns an image in the format expected by downstream nodes.
- [ ] LinkedIn and Facebook authentication and permissions work on test destinations.
- [ ] The log records the correct post ID, caption, time, and status.
- [ ] One platform failing does not leave the run looking fully successful.

## Publishing safety

This workflow can publish public content. Keep it inactive while configuring it, review generated text and images before posting, and never store access tokens in workflow JSON or Git. Revoke any token that may have been exposed in an earlier commit.

**Related files:** [Architecture](./architecture.md)
