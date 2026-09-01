# RAG Document Agent - Architecture

## System Overview

A production RAG (Retrieval-Augmented Generation) system using n8n, OpenAI, and Pinecone for enterprise document intelligence.

---

## High-Level Architecture

```mermaid
flowchart TB
    subgraph Ingestion["Ingestion Pipeline"]
        Form[Upload Form] --> Loader[PDF Document Loader]
        Loader --> Embed[OpenAI Embeddings]
        Embed --> Pinecone1[(Pinecone Index)]
    end
    
    subgraph Retrieval["Retrieval Pipeline"]
        Chat[Chat Trigger] --> Agent[AI Agent]
        Agent --> Memory[Conversation Memory]
        Agent --> Tool[Vector Store Tool]
        Tool --> Search[Similarity Search]
        Search --> Pinecone2[(Pinecone Index)]
        Pinecone2 --> Search
        Search --> Tool
    end
    
    subgraph Generation["Generation Pipeline"]
        Tool --> Context[Context Assembly]
        Context --> LLM[OpenAI GPT-4.1]
        LLM --> Agent
        Agent --> Response[Final Answer]
    end
```

---

## Data Flow

```mermaid
sequenceDiagram
    participant U as User
    participant F as Form/Chat
    participant A as AI Agent
    participant V as Vector Store
    participant L as OpenAI LLM
    
    Note over U,L: Ingestion Phase
    U->>F: Upload PDF
    F->>V: Embed and Store
    
    Note over U,L: Query Phase
    U->>A: Ask Question
    A->>L: Generate query
    A->>V: Search similar docs
    V-->>A: Return relevant chunks
    A->>L: Generate answer with context
    L-->>A: Answer
    A-->>U: Final Response
```

---

## Component Details

### 1. PDF Document Loader

- **Type**: n8n LangChain Document Loader
- **Function**: Parses PDF binary into text chunks
- **Configuration**: Default PDF loader, no special options

### 2. Embedding Model

- **Model**: text-embedding-3-small
- **Dimensions**: 1536 (default)
- **Batch Size**: 500 vectors per batch
- **Use Case**: Document and query embedding

### 3. Vector Store

- **Service**: Pinecone
- **Index Name**: n8n
- **Mode**: Insert (ingestion), Search (retrieval)
- **Distance Metric**: Cosine similarity

### 4. AI Agent

- **Type**: LangChain Agent
- **Capabilities**: Tool use, reasoning, conversation
- **Memory**: Buffer window memory for context
- **System Prompt**: Configured for helpful Q&A

### 5. Chat Model

- **Model**: gpt-4.1-mini
- **Context Window**: 128K tokens
- **Use Case**: Final answer generation
- **Tool**: Can call vector store for retrieval

---

## Index Schema

### Pinecone Index

```
Index Name: n8n
Dimensions: 1536
Metric: cosine
Pod Type: starter (can scale to production)

Vector Metadata:
- text: Original text chunk
- source: Document name
- page: Page number
- upload_date: When added
```

---

## Memory Management

```mermaid
flowchart LR
    A[User Message] --> B[Memory Check]
    B --> C{Context Available?}
    C -->|Yes| D[Add to Context]
    C -->|No| E[Fresh Start]
    D --> F[Generate Response]
    E --> F
    F --> G[Update Memory]
```

---

## Configuration

### Required Environment Variables

```env
OPENAI_API_KEY=
PINECONE_API_KEY=
PINECONE_INDEX_NAME=n8n
```

### Required Credentials

- OpenAI API (for both embeddings and chat)
- Pinecone API

---

## Security Considerations

1. **API Key Storage**: All keys in n8n credentials vault
2. **Index Isolation**: Dedicated index for this application
3. **Access Control**: Chat endpoint can be public or restricted
4. **Data Encryption**: Pinecone encrypts data at rest
5. **Audit Logging**: n8n execution logs available

---

## Performance Considerations

- **Embedding Latency**: ~200-500ms per chunk
- **Search Latency**: ~50-100ms for top-k retrieval
- **LLM Latency**: ~1-3s for answer generation
- **Throughput**: Can process multiple queries in parallel
- **Index Limits**: Pinecone starter plan has vector limits

---

## Hallucination Prevention

Strategies implemented:

1. **Grounded Context**: Answers based on retrieved documents only
2. **Tool Restriction**: Agent instructed to use vector store
3. **Empty Retrieval Handling**: Explicit "not found" responses
4. **Memory Context**: Conversation aware for clarifications
- **Future**: Add confidence scores and source citations
