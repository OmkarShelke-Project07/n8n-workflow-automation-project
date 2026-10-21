# n8n Workflow Automation Projects

A practical portfolio of workflow automations built with **n8n, AI models, APIs, and business tools**. Each project includes an importable workflow export, a project guide, and an architecture note.

The examples cover document processing, lead follow-up, document Q&A, team briefings, and social content. They are portfolio demos: connect your own accounts, review the configuration, and test with sample data before using them in a real process.

![Validate Workflows](https://github.com/OmkarShelke-Project07/n8n-workflow-automation-project/actions/workflows/validate.yml/badge.svg)

## Projects

| # | Project | Use case | Main tools |
|---|---|---|---|
| 01 | [AI Invoice Processing](./workflows/01-ai-invoice-processing/) | Extract invoice fields, check required values and possible duplicates, and route records for processing or review | n8n, Gemini, Google Drive, Sheets, Gmail |
| 02 | [AI Lead Qualification](./workflows/02-ai-lead-qualification/) | Start an AI voice call for an eligible lead and record call outcomes | n8n, Vapi, Google Sheets, webhooks |
| 03 | [RAG Document Agent](./workflows/03-rag-document-agent/) | Index PDF content and answer questions using retrieved document passages | n8n, OpenAI, Pinecone |
| 04 | [AI Lead Capture](./workflows/04-ai-lead-capture/) | Capture an enquiry, draft a welcome email, save the lead, and notify the team | n8n, Gemini, Google Sheets, Gmail, Slack |
| 05 | [Department Intelligence Agent](./workflows/05-department-intelligence-agent/) | Summarise news items and send department-specific email briefings | n8n, RSS, Gemini, Gmail |
| 06 | [AI Content Generation](./workflows/06-ai-content-generation/) | Generate social copy and image prompts, publish to configured platforms, and log results | n8n, Gemini, Pollinations.ai, LinkedIn, Facebook, Google Sheets |

## Get started

1. **Choose a project.** Read the README inside its folder before importing the JSON.
2. **Import the workflow.** In n8n, use the workflow import option and select that project's `workflow.json`.
3. **Reconnect your accounts.** The public exports do not include saved n8n credential references. Select your own credentials for the relevant nodes.
4. **Replace placeholders.** Values such as `YOUR_GOOGLE_SHEET_ID`, `YOUR_GOOGLE_DRIVE_FOLDER_ID`, and `YOUR_LINKEDIN_PERSON_ID` are examples, not working resource IDs.
5. **Test before enabling.** Use a test sheet, safe sample files, and accounts/numbers you control. Confirm the results in each connected service before activating the workflow.

All exported workflows are inactive by default. Some projects need additional setup beyond credentials; read the project's **Configuration** section.

## Environment variables

Most integrations should use n8n's credential store. Two workflows also use environment expressions in HTTP requests:

- **AI Lead Qualification:** `VAPI_ACCESS_TOKEN`, `VAPI_ASSISTANT_ID`, and `VAPI_PHONE_NUMBER_ID`.
- **AI Content Generation:** `FACEBOOK_PAGE_ID` and `FACEBOOK_ACCESS_TOKEN`.

The relevant n8n runtime must permit environment-variable access in expressions for these expressions to work. If your n8n plan or hosting setup does not permit this, replace the expressions with supported credential-based configuration. Never place real tokens in a workflow export or commit a populated `.env` file.

See [deployment notes](./docs/deployment/deployment-guide.md) and [security practices](./docs/security/security-practices.md).

## Repository structure

```text
workflows/
  01-ai-invoice-processing/
  02-ai-lead-qualification/
  03-rag-document-agent/
  04-ai-lead-capture/
  05-department-intelligence-agent/
  06-ai-content-generation/
docs/
  architecture/
  deployment/
  security/
  testing/
tests/
  invoice-processing/
  lead-qualification/
  rag-agent/
```

Each project folder contains a `workflow.json`, a project README, and an architecture note. Test case matrices are currently included for invoice processing, lead qualification, and the RAG agent.

## Validation

The GitHub Actions workflow checks JSON syntax, basic workflow structure, inactive exports, expected README files, and several common secret patterns. **These checks do not execute the workflows or prove that live API integrations work.** Run the manual checks in each project guide after importing.

## Security note

The latest exports have had saved credential references and identified account-specific resource values removed or replaced with placeholders. The social content export previously contained a hard-coded Facebook token; removing it from the current file does not remove it from earlier Git commits. **Revoke/rotate any token that may have been exposed**, and review Git history if the repository is shared.

## About

Maintained by [Omkar Shelke](https://github.com/OmkarShelke-Project07).

Licensed under the [MIT License](./LICENSE).
