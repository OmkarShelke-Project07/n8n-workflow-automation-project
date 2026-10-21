# RAG Document Agent

A retrieval-augmented generation (RAG) workflow that indexes PDF content in a Pinecone vector store and uses retrieved passages to help answer questions about the document.

## At a glance

- **Input:** A PDF for indexing and a question submitted through the n8n chat trigger.
- **Processing:** Extract/load document content, split it into chunks, create embeddings, retrieve relevant passages, and pass the retrieved context to a chat model.
- **Output:** A generated answer based on the retrieved document context.
- **Tools:** n8n, OpenAI embeddings and chat model, Pinecone vector store.

## Workflow outline

**Index a document**

`PDF upload → Load document → Split into chunks → Create embeddings → Store vectors in Pinecone`

**Ask a question**

`Chat question → Retrieve relevant vectors → Add context to the chat model → Generate answer`

The exported workflow contains nodes for both document ingestion and chat-based question answering. Retrieved context can improve relevance, but it does not guarantee correctness or prevent the model from making mistakes.

## Configuration

1. Import `workflow.json` into n8n.
2. Add your OpenAI and Pinecone credentials to the relevant nodes.
3. Configure the Pinecone index. Verify that its vector dimension and metric are compatible with the selected embedding configuration.
4. Review the document loader, chunking settings, chat trigger, and memory settings.
5. Upload a small, non-confidential PDF, run the ingestion path, and then ask questions whose answers you can check in the source.

The current project notes reference `text-embedding-3-small` and `gpt-4.1-mini`; confirm the exact model selections in n8n before running the export.

## Manual test checklist

- [ ] Ask a question whose answer is clearly present in the document.
- [ ] Ask a question that the document does not answer and check whether the response communicates uncertainty.
- [ ] Ask a question that requires details from separate sections of the document.
- [ ] Test an empty or unreadable document and review the error behavior.
- [ ] Confirm that the indexed content belongs to the intended Pinecone index.

## Notes and limitations

- Treat answers as assistance, not as a replacement for checking the source document.
- Do not upload confidential documents to external services unless the data handling arrangements allow it.
- Useful next improvements include page/source references, a retrieval relevance threshold, re-indexing updated documents, and support for DOCX/TXT.

**Related files:** [Architecture](./architecture.md) · [Test cases](../../tests/rag-agent/test-cases.md)
