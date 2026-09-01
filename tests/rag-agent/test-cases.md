# RAG Agent Tests

## Test Cases

| Test ID | Test Case | Input | Expected Result | Status |
|---------|-----------|-------|-----------------|--------|
| RAG-001 | Upload valid PDF | PDF document | Vectors stored | Manual |
| RAG-002 | Ask about content | Question about doc | Accurate answer | Manual |
| RAG-003 | Ask unrelated | Off-topic question | "Not found" response | Manual |
| RAG-004 | Multiple docs | Multiple PDFs | Cross-doc retrieval | Manual |
| RAG-005 | Chat memory | Follow-up question | Context maintained | Manual |
| RAG-006 | Empty PDF | No content | Error handling | Manual |
| RAG-007 | Large PDF | 100+ pages | Chunked properly | Manual |

## Test Scenarios

### Ingestion
1. Upload PDF via form
2. Verify text extraction
3. Verify embeddings created
4. Verify Pinecone storage

### Query
1. Ask question via chat
2. Verify vector search
3. Verify answer generation
4. Verify context maintained

### Edge Cases
1. Ambiguous questions
2. Questions requiring multiple docs
3. Questions with no answer in docs
4. Hallucination attempts
