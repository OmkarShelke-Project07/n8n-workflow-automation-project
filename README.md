# My n8n Workflow Projects

This repo is where I keep the n8n workflows I've been building for different automation tasks, from invoice processing and lead follow-up to asking questions about PDFs and creating social posts.

I'm using these projects to practise connecting AI models, APIs, and everyday business tools in one workflow. Each project has its own folder with the workflow export and notes about how it works.

These are portfolio demos, so you'll need your own n8n instance, accounts, credentials, and resource IDs before running them.

**Tools I use across these projects:** n8n, Google Gemini, OpenAI, Pinecone, Vapi, Google Workspace, webhooks, and REST APIs.

---

## Projects

| Project | What it does | Main tools |
|---|---|---|
| [AI Invoice Processing](./workflows/01-ai-invoice-processing/) | Reads invoice details, checks the extracted data, and records the result | Gemini, Drive, Sheets, Gmail |
| [AI Lead Qualification](./workflows/02-ai-lead-qualification/) | Calls a lead and records the call outcome | Vapi, Sheets, webhooks |
| [RAG Document Agent](./workflows/03-rag-document-agent/) | Lets a user ask questions about uploaded documents | OpenAI, Pinecone |
| [AI Lead Capture](./workflows/04-ai-lead-capture/) | Saves a new enquiry, drafts a welcome email, and notifies the team | Gemini, Gmail, Sheets, Slack |
| [Department Intelligence](./workflows/05-department-intelligence-agent/) | Collects AI news and sends summaries to different teams | Gemini, RSS, Gmail |
| [AI Content Generation](./workflows/06-ai-content-generation/) | Creates social media copy and sends posts to publishing platforms | Gemini, LinkedIn, Facebook, Sheets |

---

## How the workflows are put together

Most of them follow a similar pattern: a trigger starts the workflow, the incoming data is checked and formatted, an AI model or API does its part, and the result is saved or sent somewhere.

The details are different for each project. Some use a form or a manual trigger; others use a schedule or webhook.

## Running a workflow

1. Open the project folder and read its README first.
2. Use n8n Cloud or your own n8n instance.
3. Import the workflow JSON file.
4. Add your own credentials in n8n and replace any example IDs or placeholders.
5. Test it with sample data before turning it on.

More setup notes are in the [setup guide](./docs/setup.md). There are also guides for [deployment](./docs/deployment/deployment-guide.md), [security](./docs/security/security-practices.md), [testing](./docs/testing/testing-strategy.md), and the [overall structure](./docs/architecture/overview.md).

## Credentials and security

The [.env.example](./.env.example) file shows the kinds of settings these workflows may need. It is only a reference; it doesn't contain working credentials.

Please add your own credentials through n8n instead of putting API keys or tokens in workflow files. The exports in the current main branch are intended to be sanitized, but older commits may still contain values that were removed later. If a real key was ever exposed, revoke it and create a new one. More details are in the [security guide](./docs/security/security-practices.md).

## Workflow checks

The GitHub Actions workflow checks the exported files for valid JSON, expected workflow structure, secret-like values, project READMEs, and the workflow count.

![Validate Workflows](https://github.com/OmkarShelke-Project07/n8n-workflow-automation-project/actions/workflows/validate.yml/badge.svg)

## Project notes and tests

| Workflow | Notes | Architecture | Test cases |
|---|---|---|---|
| AI Invoice Processing | [README](./workflows/01-ai-invoice-processing/README.md) | [Diagram](./workflows/01-ai-invoice-processing/architecture.md) | [Tests](./tests/invoice-processing/test-cases.md) |
| AI Lead Qualification | [README](./workflows/02-ai-lead-qualification/README.md) | [Diagram](./workflows/02-ai-lead-qualification/architecture.md) | [Tests](./tests/lead-qualification/test-cases.md) |
| RAG Document Agent | [README](./workflows/03-rag-document-agent/README.md) | [Diagram](./workflows/03-rag-document-agent/architecture.md) | [Tests](./tests/rag-agent/test-cases.md) |
| AI Lead Capture | [README](./workflows/04-ai-lead-capture/README.md) | [Diagram](./workflows/04-ai-lead-capture/architecture.md) | — |
| Department Intelligence | [README](./workflows/05-department-intelligence-agent/README.md) | [Diagram](./workflows/05-department-intelligence-agent/architecture.md) | — |
| AI Content Generation | [README](./workflows/06-ai-content-generation/README.md) | [Diagram](./workflows/06-ai-content-generation/architecture.md) | — |

## About

I'm Omkar Shelke. You can find my other projects on [GitHub](https://github.com/OmkarShelke-Project07).

## License

This project is licensed under the MIT License. See [LICENSE](./LICENSE).
