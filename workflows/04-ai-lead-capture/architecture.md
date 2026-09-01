# AI Lead Capture - Architecture

## System Overview

Automated lead capture system with AI-generated personalized responses.

---

## Component Architecture

```mermaid
flowchart LR
    subgraph Input["Input"]
        Form[n8n Form]
    end
    
    subgraph Processing["Processing"]
        Store[Sheet Storage]
        AI[AI Agent]
        Gemini[Gemini Model]
        Memory[Memory Buffer]
    end
    
    subgraph Output["Output"]
        Email[Gmail]
        Slack[Slack]
    end
    
    Form --> Store
    Store --> AI
    AI --> Gemini
    Gemini --> Memory
    Memory --> AI
    AI --> Email
    Email --> Slack
```

---

## Data Flow

```mermaid
sequenceDiagram
    participant U as User
    participant F as Form
    participant S as Sheets
    participant A as AI Agent
    participant G as Gemini
    participant E as Gmail
    participant L as Slack
    
    U->>F: Submit Form
    F->>S: Save Lead Data
    S->>A: Trigger Email Gen
    A->>G: Generate Email
    G-->>A: Email Content
    A->>E: Send Welcome
    E->>L: Notify Team
```

---

## Configuration

### Required Environment Variables

```env
SHEET_LEAD_DATA_ID=
NOTIFICATION_EMAIL=
```

### Required Credentials

- Google Sheets OAuth2 API
- Gmail OAuth2 API
- Slack OAuth2 API
- Google Gemini (PaLM API)

---

## Security

1. **Email Validation**: Form validates email format
2. **OAuth2**: All Google/Slack use OAuth2
3. **Data Privacy**: Lead data stored securely
4. **Rate Limiting**: n8n execution limits apply
