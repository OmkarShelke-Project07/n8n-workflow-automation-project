# Department Intelligence Agent - Architecture

## System Overview

Automated weekly news briefing system that aggregates, analyzes, and distributes industry news to different departments.

---

## Component Architecture

```mermaid
flowchart TB
    subgraph Trigger["Trigger"]
        Schedule[n8n Schedule]
    end
    
    subgraph Fetch["News Fetch"]
        RSS[Google News RSS]
    end
    
    subgraph Process["Processing"]
        Agent[AI Agent]
        Gemini[Gemini Model]
        Parser[Output Parser]
        Split[Data Splitter]
    end
    
    subgraph Deliver["Delivery"]
        E1[Email Dev]
        E2[Email Data]
        E3[Email Content]
        E4[Email Finance]
    end
    
    Schedule --> RSS
    RSS --> Agent
    Agent --> Gemini
    Gemini --> Parser
    Parser --> Split
    Split --> E1
    Split --> E2
    Split --> E3
    Split --> E4
```

---

## News Categories

| Category | Department | Focus |
|----------|------------|-------|
| Software Development | Engineering | Tech news, tools, frameworks |
| Data Analytics | Analytics | BI, ML, data science |
| Content & Design | Creative | UX, content, design |
| Finance | Finance | Business, fintech, economics |

---

## Configuration

### Required Environment Variables

```env
NOTIFICATION_EMAIL=
```

### RSS Feed

```
https://news.google.com/rss/search?q=Artificial+Intelligence
```

---

## Output Schema

```json
{
  "Software Development": "...",
  "Data Analytics": "...",
  "Content & Design": "...",
  "Finance": "..."
}
```

---

## Security

1. **RSS Source**: Public news feed
2. **Email Delivery**: OAuth2 Gmail
3. **No Personal Data**: Only news content
