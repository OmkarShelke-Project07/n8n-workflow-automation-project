# AI Automation Engineering Portfolio

A collection of hands-on **n8n AI automation workflows** demonstrating workflow orchestration, LLM integrations, RAG, voice AI, API integrations, document processing, lead automation, research automation, and content workflows.

> **Portfolio / demo repository** — workflows are provided as reusable examples and require your own credentials, resource IDs, and service configuration before execution.

**n8n · AI Automation · LLMs · RAG · AI Agents · REST APIs · Webhooks · Google Workspace · Vapi**

---

## Projects at a glance

| Project | Business problem | AI / automation | Key integrations | Status |
|---|---|---|---|---|
| [AI Invoice Processing](./workflows/01-ai-invoice-processing/) | Manual invoice extraction and validation | Document intelligence | Gemini, Drive, Sheets, Gmail | Demo |
| [AI Lead Qualification](./workflows/02-ai-lead-qualification/) | Manual lead screening calls | Voice AI + qualification | Vapi, Sheets, Webhooks | Demo |
| [RAG Document Agent](./workflows/03-rag-document-agent/) | Manual document research | RAG + agent workflow | OpenAI, Pinecone | Demo |
| [AI Lead Capture](./workflows/04-ai-lead-capture/) | Slow lead response | AI-generated follow-up | Gemini, Gmail, Sheets, Slack | Demo |
| [Department Intelligence](./workflows/05-department-intelligence-agent/) | Manual news/research collection | AI research automation | Gemini, RSS, Gmail | Demo |
| [AI Content Generation](./workflows/06-ai-content-generation/) | Repetitive social content work | AI content generation | Gemini, LinkedIn, Facebook, Sheets | Demo |

---

## What this repository demonstrates

### AI Automation
- LLM-powered data extraction and classification
- Structured AI outputs
- Prompt-driven content generation
- Voice AI integration
- Retrieval-augmented generation
- AI-assisted decision workflows

### Workflow Engineering
- Webhook and schedule-based triggers
- REST API integration
- Data transformation and validation
- Conditional routing
- Error handling and retry-aware design
- Google Workspace integrations
- Workflow documentation and test cases

### Engineering Practices
- Sanitized workflow exports
- Environment-based configuration
- GitHub Actions validation
- Reproducible setup documentation
- Explicit demo/test status
- Security and deployment guidance

---

## Architecture pattern

Most workflows follow this reusable pattern:

```text
Trigger
   ↓
Input validation
   ↓
Transform / normalize
   ↓
AI processing
   ↓
Validation / decision
   ↓
External action
   ↓
Logging / notification
```

The exact architecture varies by project.

---

## Getting started

1. Review the project README before importing a workflow.
2. Create your own n8n instance using n8n Cloud or self-hosted n8n.
3. Import the required `workflow.json`.
4. Reconnect all n8n credentials to your own accounts.
5. Replace placeholder Sheet IDs, resource IDs, and environment-based configuration.
6. Test with sample data before activating the workflow.

Detailed guidance:

- [Setup Guide](./docs/setup.md)
- [Deployment Guide](./docs/deployment/deployment-guide.md)
- [Security Practices](./docs/security/security-practices.md)
- [Testing Strategy](./docs/testing/testing-strategy.md)
- [Architecture Overview](./docs/architecture/overview.md)

---

## Environment configuration

The repository includes [`.env.example`](./.env.example) as a reference for configuration.

Important: n8n workflow exports are **sanitized** and do not contain usable API tokens or personal email addresses. You must configure credentials in your own n8n instance.

Common configuration areas include:

- Google / Gmail / Drive / Sheets credentials
- OpenAI and Gemini credentials
- Pinecone
- Vapi
- LinkedIn
- Facebook
- Slack
- Sheet and resource IDs

---

## Security note

Never commit API keys, OAuth refresh tokens, access tokens, private webhook secrets, or production data.

The current `main` branch contains sanitized workflow exports. Some older Git history may contain values that were removed later. Any credential that was ever exposed publicly should be **revoked and replaced**, even after it has been removed from the latest files.

See [Security Practices](./docs/security/security-practices.md).

---

## CI validation

GitHub Actions validates:

- JSON syntax
- required workflow structure
- secret-like values in workflow exports
- presence of project READMEs
- workflow count

![Validate Workflows](https://github.com/OmkarShelke-Project07/n8n-workflow-automation-project/actions/workflows/validate.yml/badge.svg)

---

## Project documentation

| Workflow | README | Architecture | Tests |
|---|---|---|---|
| AI Invoice Processing | [View](./workflows/01-ai-invoice-processing/README.md) | [View](./workflows/01-ai-invoice-processing/architecture.md) | [View](./tests/invoice-processing/test-cases.md) |
| AI Lead Qualification | [View](./workflows/02-ai-lead-qualification/README.md) | [View](./workflows/02-ai-lead-qualification/architecture.md) | [View](./tests/lead-qualification/test-cases.md) |
| RAG Document Agent | [View](./workflows/03-rag-document-agent/README.md) | [View](./workflows/03-rag-document-agent/architecture.md) | [View](./tests/rag-agent/test-cases.md) |
| AI Lead Capture | [View](./workflows/04-ai-lead-capture/README.md) | [View](./workflows/04-ai-lead-capture/architecture.md) | — |
| Department Intelligence | [View](./workflows/05-department-intelligence-agent/README.md) | [View](./workflows/05-department-intelligence-agent/architecture.md) | — |
| AI Content Generation | [View](./workflows/06-ai-content-generation/README.md) | [View](./workflows/06-ai-content-generation/architecture.md) | — |

---

## Author

**Omkar Shelke**  
[GitHub](https://github.com/OmkarShelke-Project07)

---

## License

This project is licensed under the MIT License — see [LICENSE](./LICENSE).
