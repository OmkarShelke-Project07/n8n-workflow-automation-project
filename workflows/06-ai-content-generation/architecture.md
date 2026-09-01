# AI Content Generation - Architecture

## System Overview

Multi-platform social media automation using AI for content creation, image generation, and publishing.

---

## Component Architecture

```mermaid
flowchart LR
    subgraph Input["Input"]
        Trigger[Manual Trigger]
        Topic[Topic Config]
    end
    
    subgraph Generation["Content Generation"]
        LLM[LLM Chain]
        Parser[Output Parser]
        Image[Image Generator]
    end
    
    subgraph Publishing["Publishing"]
        LinkedIn[LinkedIn API]
        Facebook[Facebook API]
        Log[Sheet Logger]
    end
    
    Trigger --> Topic
    Topic --> LLM
    LLM --> Parser
    Parser --> Image
    Image --> LinkedIn
    Image --> Facebook
    LinkedIn --> Log
    Facebook --> Log
```

---

## Data Flow

```mermaid
sequenceDiagram
    participant U as User
    participant T as Trigger
    participant L as LLM
    participant P as Parser
    participant I as Image Gen
    participant LI as LinkedIn
    participant FB as Facebook
    
    U->>T: Set Topic/Brief/Tone
    T->>L: Generate Content
    L-->>P: Raw Output
    P-->>I: Image Prompt
    I-->>U: Generated Image
    P-->>LI: LinkedIn Content
    LI->>U: Post Published
    P-->>FB: Facebook Content
    FB->>U: Post Published
```

---

## Content Structure

### Input

```json
{
  "Topic": "Personal Finance",
  "Brief": "Advice on investing...",
  "Tone": "Professional"
}
```

### Output (Structured)

```json
{
  "cities": [
    "Instagram Caption...",
    "LinkedIn Caption...",
    "Facebook Caption...",
    "Hashtags...",
    "CTA...",
    "Image Prompt..."
  ]
}
```

---

## Image Generation

**Service**: Pollinations.ai (Free)

```
URL: https://image.pollinations.ai/prompt/{encoded_prompt}
Method: GET
Output: PNG image
```

---

## LinkedIn Integration

- **Endpoint**: n8n LinkedIn node
- **Content**: Caption + Hashtags
- **Media**: Generated image

---

## Facebook Integration

- **Endpoint**: Graph API v22.0
- **Method**: POST with multipart/form-data
- **Content**: Caption + Hashtags + Image URL

---

## Configuration

### Required Environment Variables

```env
SHEET_OUTPUT_LOG_ID=
FACEBOOK_PAGE_ID=
FACEBOOK_ACCESS_TOKEN=
LINKEDIN_USER_ID=
```

---

## Security Considerations

1. **API Keys**: All stored in n8n credentials
2. **Access Tokens**: Should be short-lived and rotated
3. **Sheet Permissions**: Read/write for logging only
4. **Webhook Security**: Unique IDs for all triggers

---

## Error Handling

```mermaid
flowchart TD
    E[Error] --> T{Type?}
    T -->|Input| M1[Stop Workflow]
    T -->|LinkedIn| M2[Continue to FB]
    T -->|Facebook| M3[Continue to LI]
    T -->|Image| M4[Text-only Post]
    T -->|Logging| M5[Posts Succeed]
```
