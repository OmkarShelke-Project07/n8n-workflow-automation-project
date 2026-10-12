# RAG Document Agent

This project is a document Q&A workflow built with n8n, OpenAI, and Pinecone. The goal is to let someone ask a question about a PDF and get an answer based on the document content, instead of searching through the file manually.

## How it works

There are two parts to the workflow.

**1. Add a document**

`Upload PDF → Extract text → Split into chunks → Create embeddings → Store in Pinecone`

**2. Ask a question**

`Question → Search Pinecone → Retrieve relevant text → Send context to the model → Generate an answer`

The retrieved text gives the model context for its answer. Responses should still be checked against the original document, especially when the information matters.

## Tools used

- **n8n** — connects the ingestion and chat steps
- **OpenAI embeddings** — turns text into vectors for searching
- **OpenAI chat model** — drafts an answer using retrieved context
- **Pinecone** — stores and searches the document vectors
- **n8n Chat Trigger** — receives questions

The workflow notes currently reference `text-embedding-3-small` for embeddings and `gpt-4.1-mini` for answers. Check the model settings in the exported workflow before running it.

## Input and output

- **Input:** a PDF to index, followed by a question about its content.
- **Output:** a response based on the text returned by the document search.

## Before you run it

1. Import the workflow into n8n.
2. Add your OpenAI and Pinecone credentials.
3. Set the Pinecone index and confirm its dimension matches the embedding model.
4. Check the upload and chat settings.
5. Upload a small test PDF and ask questions whose answers you can verify.

Keep credentials in n8n rather than in the exported workflow. Be careful about uploading confidential documents to external AI services.

## Cases worth checking

Ask a question clearly answered by the PDF, one that is not covered, and one that needs information from different parts of the file. Also try an empty or unreadable PDF and check how the workflow responds.

## Ideas for later

- Show the source document or page with each answer.
- Add a relevance threshold for retrieved text.
- Re-index documents when their contents change.
- Add support for formats such as DOCX and TXT.
