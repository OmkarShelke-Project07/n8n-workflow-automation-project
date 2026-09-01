# AI Automation & Workflow Engineering Portfolio

Production-oriented AI automation workflows built with n8n, LLMs, RAG, APIs, Google Workspace, and RPA technologies.

**AI Agents | Workflow Automation | RAG | LLMs | n8n | APIs | RPA**

---

## About

This portfolio demonstrates advanced AI automation engineering capabilities through six production-oriented workflows covering:

- **Document Intelligence**: AI-powered extraction and validation of structured data from unstructured documents
- **Voice AI Integration**: Automated voice-based lead qualification using Vapi AI and Gemini
- **RAG Systems**: Enterprise document intelligence with semantic search and retrieval-augmented generation
- **Lead Management**: Automated capture, qualification, and follow-up with personalized AI-generated communications
- **Business Intelligence**: Automated research and news aggregation for departmental decision-making
- **Content Automation**: Multi-platform social media content generation and publishing

Each workflow is designed with production principles: comprehensive error handling, validation, logging, human-in-the-loop approval, and scalable architecture.

---

## Featured Projects

| Project | Problem | Technologies | Automation |
|---------|---------|--------------|------------|
| [AI Invoice Processing](./workflows/01-ai-invoice-processing/) | Manual invoice data entry | n8n, Google Gemini, Google Sheets, Gmail | Document automation |
| [AI Lead Qualification](./workflows/02-ai-lead-qualification/) | Time-consuming lead screening calls | n8n, Vapi AI, Gemini, Google Sheets | Sales automation |
| [RAG Document Agent](./workflows/03-rag-document-agent/) | Manual document research | n8n, GPT-4, Pinecone, OpenAI | Knowledge automation |
| [AI Lead Capture](./workflows/04-ai-lead-capture/) | Slow lead response times | n8n, Gemini, Gmail, Slack | Lead automation |
| [Department Intelligence](./workflows/05-department-intelligence-agent/) | Manual competitive research | n8n, Gemini, Gmail | Research automation |
| [AI Content Generation](./workflows/06-ai-content-generation/) | Manual content creation | n8n, Gemini, LinkedIn, Facebook | Content automation |

---

## Tech Stack

### Automation
- **n8n** - Workflow orchestration and automation
- **Webhooks** - Event-driven triggers
- **REST APIs** - System integration
- **Cron Jobs** - Scheduled automation

### AI and LLMs
- **OpenAI GPT-4** - Language model for RAG and structured outputs
- **Google Gemini** - Multimodal AI for document processing and generation
- **Vapi AI** - Voice AI for automated calls
- **Prompt Engineering** - Task-specific prompting strategies
- **Structured Outputs** - JSON schema validation for AI responses

### RAG and Vector
- **Pinecone** - Vector database for semantic search
- **OpenAI Embeddings** - Document vectorization
- **Semantic Search** - Context-aware retrieval
- **Document Processing** - PDF extraction and chunking

### Integrations
- **Gmail** - Email notifications and communication
- **Google Drive** - File storage and management
- **Google Sheets** - Data storage and CRM
- **LinkedIn** - Professional social media publishing
- **Facebook** - Social media publishing
- **Slack** - Team notifications

### Engineering
- **JSON** - Workflow configuration
- **Git** - Version control
- **GitHub Actions** - CI/CD validation
- **Environment Variables** - Secret management

---

## Architecture

Workflows follow a consistent production architecture:

1. **Trigger** - Webhook, schedule, form, or file watch
2. **Data Processing** - Extract, transform, validate
3. **AI Processing** - LLM calls, RAG, agentic decisions
4. **Validation** - Schema check, confidence threshold
5. **Action** - Auto-process or human review
6. **Integration** - External systems (Sheets, Drive, Email)
7. **Notification** - Success, failure, or alert

---

## Security

Security is a primary concern in this portfolio:

- **No secrets committed** - All API keys, tokens, and credentials are managed via environment variables
- **.env.example provided** - Documents required variables without exposing actual values
- **.gitignore configured** - Prevents accidental commit of sensitive files
- **Least-privilege access** - Workflows use minimal required permissions
- **Webhook security** - Unique webhook IDs for each workflow
- **OAuth2** - Secure authentication with Google, Slack, and LinkedIn

### Setting Up Credentials

1. Copy .env.example to .env
2. Fill in your actual API keys and credentials
3. Configure n8n credentials using environment variable references
4. Never commit .env to version control

---

## Testing

Each workflow includes test documentation covering:

- Happy path scenarios (valid inputs)
- Edge cases (missing data, malformed inputs)
- Error handling (API failures, timeouts)
- Integration tests (end-to-end workflows)

---

## Project Documentation

| Workflow | README | Architecture |
|----------|--------|--------------|
| AI Invoice Processing | [View](./workflows/01-ai-invoice-processing/README.md) | [View](./workflows/01-ai-invoice-processing/architecture.md) |
| AI Lead Qualification | [View](./workflows/02-ai-lead-qualification/README.md) | [View](./workflows/02-ai-lead-qualification/architecture.md) |
| RAG Document Agent | [View](./workflows/03-rag-document-agent/README.md) | [View](./workflows/03-rag-document-agent/architecture.md) |
| AI Lead Capture | [View](./workflows/04-ai-lead-capture/README.md) | [View](./workflows/04-ai-lead-capture/architecture.md) |
| Department Intelligence | [View](./workflows/05-department-intelligence-agent/README.md) | [View](./workflows/05-department-intelligence-agent/architecture.md) |
| AI Content Generation | [View](./workflows/06-ai-content-generation/README.md) | [View](./workflows/06-ai-content-generation/architecture.md) |

---

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## Author

**Omkar Shelke** - GitHub: [@OmkarShelke-Project07](https://github.com/OmkarShelke-Project07)

---

*Production-oriented automation workflows designed for reliability, maintainability, and business value.*
