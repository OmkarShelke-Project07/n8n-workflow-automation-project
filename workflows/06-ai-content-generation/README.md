# AI Content Generation

This workflow uses Gemini to draft social media content from a topic and brief, then prepares posts for LinkedIn and Facebook. It also uses Pollinations.ai for an image and logs the post details in Google Sheets.

I used it to explore how much of the repeatable content workflow can be connected in n8n. The generated copy and image should still be reviewed before anything is published.

## How it works

`Enter topic and brief → Generate copy → Format the content → Create image → Publish → Log result`

The workflow is set up for platform-specific captions, hashtags, a call to action, and an image prompt. The exact publishing steps depend on the connected social accounts.

## Tools used

- **n8n** — connects the steps
- **Google Gemini** — drafts the content
- **Pollinations.ai** — generates an image
- **LinkedIn and Facebook** — publishing destinations
- **Google Sheets** — records post details

## Input and output

The input includes a topic, a short brief, and the tone to use. The workflow can prepare platform-specific copy and an image, publish through the connected accounts, and record the result in a sheet.

## Before you run it

1. Import the workflow into n8n.
2. Add your Gemini and social platform credentials.
3. Check the required fields and account permissions.
4. Test with a harmless draft or test account before publishing publicly.
5. Review the generated text and image yourself before posting.

Social platform permissions and APIs can change, so check the connected account setup if publishing fails. Don't keep access tokens in the exported workflow.

## Cases worth checking

Try a missing topic, an image-generation failure, and a failure on one of the publishing steps. Confirm what is logged and whether the other steps continue as expected.

## Ideas for later

- Add an approval step before publishing.
- Add scheduling and post-performance tracking.
- Generate image alt text.
- Test different caption styles and compare the results.
