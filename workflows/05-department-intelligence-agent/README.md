# Department Intelligence Agent

This workflow collects AI-related news from an RSS feed, uses Gemini to summarise and sort the items, and prepares email briefings for different departments.

I wanted to try a way of sending teams a shorter, more relevant update instead of asking everyone to read through the same list of news stories.

## How it works

`Weekly schedule → Read RSS feed → Summarise and categorise → Split by department → Send email`

The current workflow notes describe four categories: software development, data analytics, content and design, and finance.

## Tools used

- **n8n** — runs the scheduled workflow
- **Google News RSS** — provides the news feed
- **Google Gemini** — summarises and categorises items
- **Gmail** — sends the briefings

## Before you run it

1. Import the workflow into n8n.
2. Connect your Gemini and Gmail credentials.
3. Check the RSS feed and the department categories.
4. Review the schedule and email recipients.
5. Test with a small set of items and make sure stories reach the intended category.

The exported workflow may need changes to fit your own departments and recipients. Keep credentials and internal email addresses out of public workflow files.

## Cases worth checking

Check what happens when the feed has no items, the AI response can't be parsed, or the email step fails. Also review the summaries to make sure they reflect the source articles accurately.

## Ideas for later

- Pull from more than one news source.
- Let each team choose its own topics.
- Keep a history of earlier briefings so recurring themes are easier to spot.
